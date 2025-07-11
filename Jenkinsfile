pipeline {
    agent {
            docker {
                image 'node:18-alpine'

            }
            }

    stages {
        stage('Build') {
            
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
        stage('Test'){
            steps ('Check file') {
                
                sh '''
                cd build
                [ -f index.html ] && echo "Файл найден" || echo "Файл не найден"
                '''
                 sh '''
                npm test -- --watchAll=false
                '''
            }
           
        }
    }
}