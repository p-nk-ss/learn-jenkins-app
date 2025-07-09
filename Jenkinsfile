pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                sh 'echo "Hello jenks"'
                sh 'hostname -i'
                sh 'uname'
            }
        }
    }
}