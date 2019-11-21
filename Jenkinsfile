    pipeline {
        agent any
        stages {
            stage('Build') {
                steps {
                    echo 'Building application'
                    sh '''
                        apt-get install -y gcc-c++ make
                        curl -sL https://rpm.nodesource.com/setup_13.x | sudo -E bash -
                        yum install -y nodejs
                        npm install
                        npm run build
                    '''
                }
            }
            stage('Test') {
                steps {
                    sh 'echo "Running test"'
                    sh '''
                        npm test
                    '''
                }
            }
            stage('Code Analysis') {
                steps {
                        sh 'echo "Running tests"'
                }
            }
            stage('Deploy') {
                steps {
                    sh 'echo "Deploying"'
                }
            }
        }
    }
