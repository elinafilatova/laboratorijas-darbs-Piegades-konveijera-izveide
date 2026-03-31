pipeline {
    agent any

    stages {
        stage ('install-pip-deps') {
            steps {
                echo 'Installing all required dependencies...'
                bat 'if exist python-greetings rmdir /s /q python-greetings'
                bat 'git clone https://github.com/mtararujs/python-greetings.git'
                bat 'dir python-greetings'
                bat '''
                cd python-greetings
                C:/Users/W/AppData/Local/Programs/Python/Python313/python.exe -m venv venv
                venv\\Scripts\\python.exe -m pip install -r requirements.txt
                '''
            }
        }
        
        stage ('deploy-to-dev') {
            steps{
                script{
                    deploy("development")
                }
            }
        }

        stage ('tests-on-dev') {
            steps{
                echo 'Running tests on development..'
            }
        }

        stage ('deploy-to-stg') {
            steps{
                script{
                    deploy("staging")
                }
            }
        }

        stage ('tests-on-stg') {
            steps{
                echo 'Running tests on staging...'
            }
        }

        stage ('deploy-to-preprod') {
            steps{
                script{
                    deploy("preprod")
                }
            }
        }

        stage ('tests-on-preprod') {
            steps{
                echo 'Running tests on preprod...'
            }
        }

        stage ('deploy-to-prod') {
            steps{
                script{
                    deploy("production")
                }
            }
        }

        stage ('tests-on-prod') {
            steps{
                echo 'Running tests on production...'
            }
        }
    }
}


def deploy(String environment){
    echo "Deployment to ${environment} environment has started.."
    bat 'if exist python-greetings rmdir /s /q python-greetings'
    bat 'git clone https://github.com/mtararujs/python-greetings.git'

    echo 'pm2 delete greetings-app-${environment} & set "errorlevel=0"'

    echo "Deployment to ${environment} environment finished.."
}
