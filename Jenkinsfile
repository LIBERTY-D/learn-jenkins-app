pipeline {
    agent any

    stages {
        stage('build') {
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