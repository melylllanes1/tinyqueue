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
		sh '''
                        npm install
			
                    '''
                    echo 'Running analysis...'
                withSonarQubeEnv('sonarcloud') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }

            stage('Build2') {
              tools {
                 snyk 'SynkSecurity'
                     } 
              steps {
                snykSecurity(
                  projectName: 'project-js',
                  severity: 'high',
                  snykInstallation: 'SynkSecurity',
                  snykTokenId: 'my-projectjs-snyk-api-token',
                  targetFile: '/var/jenkins_home/index.js'
        )   
      	}                        
                }
            }


        }
    

