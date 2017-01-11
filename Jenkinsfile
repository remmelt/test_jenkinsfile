#!groovy

node {
    agent any

    parameters {
        choiceParam(choices: 'mp\nmde\nebayk', description: 'Tenant?', name: 'tenant')
    }

    stages {

        stage("Hoei") {
            steps {
                parallel (
                    "One": {
                        sh 'echo dubbele hoei'
                        sh 'sleep 3'
                        sh 'echo End ONE'
                    },
                    "Two": {
                        sh 'echo dubbele hoei2'
                        sh 'sleep 3'
                        sh 'echo End TWO'
                    },
                    "Three": {
                        sh 'echo dubbele hoei'
                        sh 'sleep 3'
                        sh 'echo End ONE'
                    },
                )
            }
        }

    }
}
