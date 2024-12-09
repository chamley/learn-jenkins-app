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
                script {
                    try {
                        sh '''
                            ls -la
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
                    } catch (Exception e) {
                        echo 'Exception occured' + e.toString()
                        sh "ls -la"
                        sh "cat /home/node/.npm/_logs/2024-12-09T14_32_01_358Z-debug-0.log"
                    }
                }
            }
        
        }
    }
}
