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
                script{
                    test("development")
                }
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
                script{
                    test("staging")
                }
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
                script{
                    test("preprod")
                }
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
                script{
                    test("production")
                }
            }
        }
    }
}


def deploy(String environment, int port){
    echo "Deployment to ${environment} environment has started.."
    bat 'C:/Users/W/AppData/Roaming/npm/pm2.cmd kill & EXIT /B 0'
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
    C:/Users/W/AppData/Roaming/npm/pm2.cmd start app.py --name greetings-app-${environment} --interpreter %CD%\\venv\\Scripts\\python.exe -- --port ${port}
    """
    bat 'C:/Users/W/AppData/Roaming/npm/pm2.cmd list'
    echo "Deployment to ${environment} environment finished.."
}


def test(String environment) {
    echo "Running tests on ${environment}..."

    bat 'if exist course-js-api-framework rmdir /s /q course-js-api-framework'
    bat 'git clone https://github.com/mtararujs/course-js-api-framework.git'

    bat """
    cd course-js-api-framework
    npm install
    npm run greetings greetings_${environment}
    """

    bat """
    cd course-js-api-framework
    npm run greetings greetings_${environment} || echo test failed
    """

    echo "Tests on ${environment} enviroment finished..."
}

