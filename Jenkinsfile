pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:22-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    npm --version
                    node --version
                    npm install
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
