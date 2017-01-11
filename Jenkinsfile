#!groovy

node {
    properties([parameters([
        choice(choices: 'mp\nebayk', description: '', name: 'tenant')
    ]), pipelineTriggers([])])

    stage("Hoei") {
        parallel (
            "One": {
                sh 'echo dubbele hoei ${tenant} -----'
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
