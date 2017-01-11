#!groovy

properties([parameters([
    string(name: 'githash', defaultValue: '43408ca'),
    choice(choices: 'mp\nebayk', name: 'tenant'),
    choice(choices: 'sandbox\nprod', name: 'target'),
])])

node {
    stage("Getv") {
        def response = httpRequest "http://repo_comaas:V9Knbsi4Nm@repositories.ecg.so/v2/files/${tenant}"
        println("Status: " + response.status)
        def jsonSlurper = new groovy.json.JsonSlurper()
        def releaseNames = jsonSlurper.parseText(response.content).keySet()
        def releaseName = '-'
        echo "${releaseNames}"
        for (name in releaseNames) {
            if (name.contains("${githash}") && name.contains("${tenant}") && name.contains("${target}")) {
                echo "Release found: ${name} ***"
                releaseName = name
            }
        }
        if (releaseName == '-') {
            error("Could not find release ${githash} for tenant ${tenant} and target env ${target} in repositories server.")
        }

        echo "---${releaseName}==="
    }
}
