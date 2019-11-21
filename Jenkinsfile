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
                    sh "${scannerHome}./var/jenkins_home/sonar-scanner/sonar-scanner-3.3.0.1492-linux"
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
