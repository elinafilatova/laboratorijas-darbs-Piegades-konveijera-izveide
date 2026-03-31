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
                    deploy("development", 7001)
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
                    deploy("staging", 7002)
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
                    deploy("preprod", 7003)
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
                    deploy("production", 7004)
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


def deploy(String environment, int port){
    echo "Deployment to ${environment} environment has started.."
    bat 'if exist python-greetings rmdir /s /q python-greetings'
    bat 'git clone https://github.com/mtararujs/python-greetings.git'
    bat "C:/Users/W/AppData/Roaming/npm/pm2.cmd delete greetings-app-${environment} & EXIT /B 0"

    bat '''
    cd python-greetings
    C:/Users/W/AppData/Local/Programs/Python/Python313/python.exe -m venv venv
    venv\\Scripts\\python.exe -m pip install -r requirements.txt
    '''

    bat """
    cd python-greetings
    C:/Users/W/AppData/Roaming/npm/pm2.cmd start app.py --name greetings-app-${environment} --interpreter ./venv/bin/python -- --port ${port}
    """

    bat 'C:/Users/W/AppData/Roaming/npm/pm2.cmd list'

    echo "Deployment to ${environment} environment finished.."
}
