pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building application"'
                 sh '''
                    sudo yum install -y gcc-c++ make
                    sudo curl -sL https://rpm.nodesource.com/setup_13.x | sudo -E bash -
                    sudo sudo yum install -y nodejs
                    node -v; npm -v
                    npm install
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
