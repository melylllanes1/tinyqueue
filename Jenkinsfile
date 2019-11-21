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
                def scannerHome = tool 'SonarQubeScanner';
                withSonarQubeEnv('sonarqube') { 
                sh "${scannerHome}/var/jenkins_home/sonar-scanner/sonar-scanner-3.3.0.1492-linux"
           }

            stage('Deploy') {
                steps {
                    echo 'Deploying...'
                }
            }
        }
    }
