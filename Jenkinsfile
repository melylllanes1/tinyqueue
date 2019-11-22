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
                    echo 'Running test...'
                    sh '''
                        npm test
                    '''
                }
            }
            stage('Code Analysis') {
                environment {
                    scannerHome = tool 'SonarQubeScanner'
                }
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh "./${scannerHome}/bin/sonar-scanner"
                }
            }
        }

            stage('Deploy') {
                steps {
                    echo 'Deploying...'
                }
            }
        }
    }
