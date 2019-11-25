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

            stage('Security with Snyk') {
              tools {
                 snyk 'SynkSecurity'
                     }
              steps {
                  echo'Running Security Analysis...'
                snykSecurity(
                  projectName: 'project-js',
                  severity: 'medium',
                  snykInstallation: 'SynkSecurity',
                  snykTokenId: 'my-projectjs-snyk-api-token'

                //  targetFile: 'prueba.js '
                         )
        }
                }

     stage('Code Analysis') {
                environment {
                    scannerHome = tool 'SonarCloud'
                }
            steps {
                    echo 'Running analysis...'
                withSonarQubeEnv('sonarcloud') {
                    sh "${scannerHome}/bin/sonar-scanner"


                }
            }
            
            }

           

            stage('Deployment') {
               steps {
                  echo  'Deploying succesful!'
                     }
                    }
            }
        }
    
