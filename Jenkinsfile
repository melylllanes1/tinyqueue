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
			npm install -g typescript
                    '''
                    echo 'Running analysis...'
                withSonarQubeEnv('sonarcloud') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }

            stage('Build2') {
                      environment {
                          SNYK_TOKEN = credentials 'my-project-snyk-api-token'
                          } 
                
                steps {
                    echo 'Running test...'
                  sh """ 
                 
                  snyk auth ${SNYK_TOKEN}
                  snyk test --json \
                    --severity-threshold=high \
                    --file=index.js \
                    --org=cloudbees \
                    --project-name=project-js
                """  


                }
            }


        }
    }

