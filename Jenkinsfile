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
                    script {
                        scannerHome = tool 'SonarQubeScanner'
                         sh "echo ${scannerHome}"
                    }
                    withSonarQubeEnv('sonarqube') {
                    sh "${scannerHome}"
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
