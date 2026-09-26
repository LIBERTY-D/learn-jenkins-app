pipeline {
    agent any

    stages {
  
        stage('w/o docker') {
            steps {
                sh '''
                echo "without docker"
                touch container-no.txt
                '''
            }
        }
        
        stage('w/ docker') {
            agent {
                docker {
                    image "node:18-alpine"
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo "with docker"
                npm --version
                touch container-yes.txt
                '''
            
            }
        }
    }
}