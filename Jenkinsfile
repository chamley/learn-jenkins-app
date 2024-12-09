pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    docker --version
                    npm --version
                    node --version
                    npm ci
                    npm run build
                    ls -la
                    git checkout -B 'tempbranch'
                    git status
                    touch hello.txt
                    git status
                    git commit -m 'commit from pipeline'
                    git push --set-upstream origin tempbranch
                '''
            }
        
        }
    }
}
