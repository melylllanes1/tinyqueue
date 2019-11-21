    pipeline {
        agent any
        stages {
            stage('Build') {
                steps {
                    echo 'Building application'
                    sh '''
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
            stage('Code' ) {
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

