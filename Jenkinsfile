#!groovy



node {
    properties([parameters([
        string(name: 'githash', defaultValue: 'aaa1111'),
        choice(choices: 'mp\nebayk', name: 'tenant'),
        choice(choices: 'sandbox\nprod', name: 'env'),
    ])])

    stage("Getv") {
        def response = httpRequest "http://repo_comaas:V9Knbsi4Nm@repositories.ecg.so/v2/files/${tenant}"
        println("Status: "+response.status)
        def jsonSlurper = new groovy.json.JsonSlurper()
        def object = jsonSlurper.parseText(response.content).keySet()
        // def h = object.name
        echo "---${object}==="
    }
}
