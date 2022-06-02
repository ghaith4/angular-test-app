pipeline
{
    agent any 
        stages {
            stage('Pull'){
                steps{
                    script{
                        checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                            userRemoteConfigs: [[
                                credentialsId: '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',
                                url: 'https://github.com/ghaith4/angular-test-app.git'
                            ]]]
                        )
                    }
                }
            }
            stage('Build'){
                steps{
                    script{
                        sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.ini"
                    }
                }
            }
        }
}