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
                steps {
                    environment {
                        scannerHome = tool 'SonarQubeScanner'
                         sh "echo ${scannerHome}"
                    }
                    withSonarQubeEnv('sonarqube') {
                    //sh """${scannerHome}/bin/sonnar-scanner"""
		    sh '''
			cd /var/jenkins_home/sonar-scanner/sonar-scanner-3.3.0.1492-linux/bin
                        ./sonar-scanner
			'''

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
