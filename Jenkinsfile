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
                    scannerHome = tool 'sonascanner'
                }
                steps {
                    withSonarQubeEnv('sonarqube') {
                    sh "${scannerHome}.docker.image('newtmitch/sonar-scanner').inside('-v /var/run/docker.sock:/var/run/docker.sock')"




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
