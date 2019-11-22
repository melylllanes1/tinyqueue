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
                    scannerHome = tool 'SonarCloud'
                }
            steps {
                    echo 'Running analysis...'
                withSonarQubeEnv('sonarcloud') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
            stage('snyk dependency scan') {
                steps {
                    echo 'Deploying...'
                  // snykSecurity(
                      snykSecurity organisation: 'berenicehdr',
                   // snykSecurity projectName: 'project-js',
                      severity: 'high',
                      snykInstallation: 'SynkSecurity',
                      snykTokenId: 'my-project-snyk-api-token',
                      targetFile: 'index.js' 
                     // sh ' snyk auth', 
                      sh ' snyk test --json '            
                }
           }
        }
    }
