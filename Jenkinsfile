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
    }
    
    post {
            always{
                junit 'test-results/junit.xml'
            }
        }
}