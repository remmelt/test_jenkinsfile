#!groovy

properties([parameters([
    string(name: 'githash', defaultValue: '43408ca'),
    choice(choices: 'sandbox\nprod', name: 'target_env'),
    choice(choices: 'mp\nebayk', name: 'tenant'),
])])

node {
    stage("Getv") {
        echo "${tenant}"
        echo "${target_env}"
        def response = httpRequest "http://repo_comaas:V9Knbsi4Nm@repositories.ecg.so/v2/files/${tenant}"
        println("Status: " + response.status)
        def jsonSlurper = new groovy.json.JsonSlurper()
        def releaseNames = jsonSlurper.parseText(response.content).keySet()
        def releaseName = '-'
        echo "${releaseNames}"
        for (name in releaseNames) {

// Release found: /mp/prod/20170111-1554/comaas-mp_prod-20170111-1554-df2297a.tar.gz ***

            if(name ==~ /.*\/comaas-${tenant}_{target_env}-\d+-\d+-${githash}\.tar.gz/) {
            // if (name.contains("comaas-${tenant}") && name.contains("${tenant}") && name.contains("${target_env}")) {
                echo "Release found: ${name} ***"
                releaseName = name
            }
        }
        if (releaseName == '-') {
            error("Could not find release ${githash} for tenant ${tenant} and target env ${target_env} in repositories server.")
        }

        echo "---${releaseName}==="
    }
}
