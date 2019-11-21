pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building application"'
                 sh '''
                    npm run build
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running test"'
                 sh '''
                    npm test
                '''
            }
        }
         stage('Code Analysis') {
            steps {
                    sh 'echo "Running tests"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying"'
            }
        }
    }
}
