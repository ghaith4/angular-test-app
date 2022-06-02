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
            stage('Create Docker Image'){
                steps{
                    script{
                        sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.ini"
                    }
                }
            }
            stage('Push Image to Docker Hub'){
                steps{
                    script{
                        sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.ini"
                    }
                }
            }
        }
}