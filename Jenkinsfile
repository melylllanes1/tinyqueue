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
                    }
                    withSonarQubeEnv('sonarqube') {
                    sh "${scannerHome}/var/jenkins_home/sonar-scanner/sonar-scanner-3.3.0.1492-linux"
                }
              }
           }

 /*           stage('Deploy') {
                       tools {
                         snyk 'snyk-latest'
                  } 
                       steps {
                         snykSecurity(
          		 snykSecurity failOnIssues: false,
           		 projectName: 'proyecto-js',
           		 snykInstallation: 'Please define a Snyk installation in the Jenkins Global Tool Configuration. This task will not run without a Snyk installation.',
          		 snykTokenId: 'my-org-snyk-api-token', 
          		 targetFile: 'https://github.com/melylllanes1/tinyqueue.git'

        )   
      }
            } /*
        }
    }


