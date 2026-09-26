pipeline {
    agent any

    environment{
        MY_APP_CONFIG ='TEST'
    }
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
              agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
             steps{
                sh '''
                  test -f build/index.html
                  npm test

                '''
             }
        }
  
        stage("Deploy"){
              agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
             steps{
                sh '''
                  npm install -g netlify-cli
                  netlify --version
                  echo $MY_APP_CONFIG 
                '''
             }
        }
    }
    post {
    always {
        junit 'test-results/junit.xml'
    }
}
}