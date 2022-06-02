pipeline
{
    agent any 
    tools {nodejs "node"}
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
                        sh "npm install"
                        sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.ini"
                    }
                }
            }
            stage('Docker'){
                steps{
                    script{
                        sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.ini"
                    }
                }
            }
        }
}