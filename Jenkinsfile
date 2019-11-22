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
 /*           stage('Code Analysis') {
                environment {
                    scannerHome = tool 'SonarQubeScanner'
                }
            steps {
                    echo 'Running analysis...'
                withSonarQubeEnv('sonarqube') {
                    // sh "${scannerHome}/bin/sonar-scanner"
                     sh '''
                        cd /var/jenkins_home/sonar-scanner/sonar-scanner-3.3.0.1492-linux/bin
                        pwd
                        ./sonar-scanner
                    '''
                }
            }
        }
*/
            stage('Deploy') {
                steps {
                    echo 'Deploying...'
                }
            }
        }
    }
