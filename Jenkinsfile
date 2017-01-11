#!groovy

node {
    properties([parameters([
        choice(choices: 'mp\nebayk', description: '', name: 'tenant'),
        choice(choices: 'sandbox\nprod', description: '', name: 'env'),
    ]), pipelineTriggers([])])

    stage("Hoei") {
        def response = httpRequest 'http://localhost:8080/jenkins/api/json?pretty=true'
        println("Status: "+response.status)
        println("Content: "+response.content)
    }
}
