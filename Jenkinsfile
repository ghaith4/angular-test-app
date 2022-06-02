pipeline
{
    agent any 
    tools {nodejs "nodeJS"}
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
                        sh "npm install"
                    }
                }
            }
        }
}