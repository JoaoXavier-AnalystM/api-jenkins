pipeline {
    agent any

    stages {

        stage('Checkout Source') {
            steps {
                git url: 'https://github.com/JoaoXavier-AnalystM/teste_api.git/', branch: 'master'
            }
        }        
        
        stage('Docker Build Image') {
            steps {
                script {
                    dockerapp = docker.build("joaotixavier/testeapi:${env.BUILD_ID}",
                      )
                }
            }
        }

        stage('Docker Push Image') {
            steps {
                script {
                        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }
    }
}