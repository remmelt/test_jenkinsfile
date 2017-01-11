#!groovy

properties([parameters([
    string(name: 'githash', defaultValue: '1e0bffc'),
    choice(choices: 'master\nmp\nebayk', name: 'tenant'),
    choice(choices: 'sandbox\nprod', name: 'env'),
])])

node "${tenant}" {
    stage("Getv") {
        def response = httpRequest "http://repo_comaas:V9Knbsi4Nm@repositories.ecg.so/v2/files/${tenant}"
        println("Status: " + response.status)
        def jsonSlurper = new groovy.json.JsonSlurper()
        def releaseNames = jsonSlurper.parseText(response.content).keySet()
        def releaseName = '-'
        for (name in releaseNames) {
            if (name.contains(${githash})) {
                echo "Release found: ${name} ***"
                releaseName = name
            }
        }
        if (releaseName == '-') {
            error("Could not find release ${githash} for tenant ${tenant} in repositories server.")
        }

        echo "---${releaseName}==="
    }
}
