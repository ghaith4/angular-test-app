pipeline
{
    agent any 
    tools {
        nodejs "node",
        docker "docker"
        }
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
                        sh "pip install docker"
                        sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.ini"
                    }
                }
            }
        }
}