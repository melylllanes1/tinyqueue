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
            stage('snyk dependency scan') {
                steps {
                    echo 'Deploying...'

                    sh ' snyk test --json '
                   // sh '''
                    //snyk test https://github.com/melylllanes1/tinyqueue.git
                      //  '''
                    snykSecurity organisation: 'berenicehdr',
                   // snykSecurity projectName: 'project-js',
                    severity: 'high',
                    snykInstallation: 'SynkSecurity',
                    snykTokenId: 'my-project-snyk-api-token',
                    targetFile: 'index.js'
                }
            }
        }
    
}
