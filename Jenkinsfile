pipeline {
    agent any
    stages {
        stage('w/o docker') {
            steps {
                sh '''
                    echo without docker
                    ls -la
                    touch container-no.text
                
                '''
            }
        }
        stage('w docker') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo with docker
                    npm --version
                    ls -la
                    touch container-yes.text
                '''
            }
        }
    }
}
