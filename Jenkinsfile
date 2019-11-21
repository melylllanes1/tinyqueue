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
            stage('Sonarqube') {
                environment {
                    scannerHome = tool 'sonarscanner'
                }
                steps {
                    withSonarQubeEnv('sonarqube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
                timeout(time: 10, unit: 'MINUTES') {
                     waitForQualityGate abortPipeline: true
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
