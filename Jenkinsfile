#!groovy

def jsonSlurper = new groovy.json.JsonSlurper()
def object = jsonSlurper.parseText('{ "name": "John Doe" }')
def h = object.name

node {
    properties([parameters([
        string(name: 'githash', defaultValue: 'aaa1111'),
        choice(choices: 'mp\nebayk', name: 'tenant'),
        choice(choices: 'sandbox\nprod', name: 'env'),
    ])])

    stage("Hoei") {
        def response = httpRequest 'http://google.com/'
        println("Status: -${h}- "+response.status)
        println("Content: "+response.content)
    }
}
