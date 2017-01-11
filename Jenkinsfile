#!groovy

def jsonSlurper = new groovy.json.JsonSlurper()
def object = jsonSlurper.parseText('{ "name": "John Doe" } /* some comment */')
def h = object.name

node {
    properties([parameters([
        string(name: 'githash'),
        choice(choices: 'mp\nebayk', name: 'tenant'),
        choice(choices: 'sandbox\nprod', name: 'env'),
    ])])

    stage("Hoei") {
        def response = httpRequest 'http://localhost:8080/jenkins/api/json?pretty=true'
        println("Status: -${h}- "+response.status)
        println("Content: "+response.content)
    }
}
