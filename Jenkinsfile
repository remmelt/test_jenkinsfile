#!groovy

node {
    properties([parameters([
        string(name: 'githash'),
        choice(choices: 'mp\nebayk', name: 'tenant'),
        choice(choices: 'sandbox\nprod', name: 'env'),
    ]), pipelineTriggers([])])

    stage("Hoei") {
        def response = httpRequest 'http://localhost:8080/jenkins/api/json?pretty=true'
        println("Status: "+response.status)
        println("Content: "+response.content)
    }
}
