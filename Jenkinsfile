pipeline {
    
    agent any

    stages {
    //     stage('Build') {
            
    //         steps {
    //             sh '''
    //                 ls -la
    //                 node --version
    //                 npm --version
    //                 npm ci
    //                 npm run build
    //                 ls -la
    //             '''
    //         }
    //     }

        
        stage('Test'){
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps ('Check file') {
                
                sh '''
                npm --version
                cd build
                [ -f index.html ] && echo "Файл найден" || echo "Файл не найден"
                '''
                //  sh '''
                // npm test -- --watchAll=false
                // '''
            }
           
        }
        stage('E2E'){
            agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.54.0-noble'
                    reuseNode true
                }
            }
            steps ('Check file') {
                
                sh '''
                    npm install serve
                    node_modules/.bin/serve -s build &
                    sleep 10
                    npx playwright test
                '''

            }
           
        }
    }
    
    post {
            always{
                junit 'test-results/junit.xml'
            }
        }
}