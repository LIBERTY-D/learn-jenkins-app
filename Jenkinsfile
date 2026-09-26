pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                  ls -la
                  node --version
                  npm --version
                  npm ci
                  npm run build
                  ls -la

                '''
            }
        }
        stage("Test"){
             steps{
                sh '''
                  echo "test stage"

                '''
             }
        }
  
        // stage('w/o docker') {
        //     steps {
        //         sh '''
        //         echo "without docker"
        //         touch container-no.txt
        //         '''
        //     }
        // }
        
        // stage('w/ docker') {
        //     agent {
        //         docker {
        //             image "node:18-alpine"
        //             reuseNode true
        //         }
        //     }
        //     steps {
        //         sh '''
        //         echo "with docker"
        //         npm --version
        //         touch container-yes.txt
        //         '''
            
        //     }
        // }
    }
}