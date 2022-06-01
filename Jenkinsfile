pipeline
{
    agent any
    stages {
        stage('Pull'){
            steps{
                script{
                    checkout([$class: 'GitSCM', branches:[[name:'*/main']],
                        userRemoteConfigs: [[
                            credentialsId: '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',
                            url: 'https://github.com/ghaith4/angular-test-app.git'
                        ]]])
                }
            }
        }
    }
}
