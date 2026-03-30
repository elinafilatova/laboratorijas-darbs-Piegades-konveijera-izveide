pipeline {
    agent any

    stages {
        stage ('install-pip-deps') {
            steps {
                echo 'Installing all required dependencies...'
                bat 'if exist python-greetings rmdir /s /q python-greetings'
                bat 'git clone https://github.com/mtararujs/python-greetings.git'
                bat 'cd python-greetings && dir'
                bat 'cd python-greetings && C:/Users/W/AppData/Local/Microsoft/WindowsApps/python.exe -m venv venv'
            }
        }
        
        stage ('deploy-to-dev') {
            steps{
                echo 'Deploying to a development...'
            }
        }

        stage ('tests-on-dev') {
            steps{
                echo 'Running tests on development..'
            }
        }

        stage ('deploy-to-stg') {
            steps{
                echo 'Deploying to a staging...'
            }
        }

        stage ('tests-on-stg') {
            steps{
                echo 'Running tests on staging...'
            }
        }

        stage ('deploy-to-preprod') {
            steps{
                echo 'Deploying to a preprod...'
            }
        }

        stage ('tests-on-preprod') {
            steps{
                echo 'Running tests on preprod...'
            }
        }

        stage ('deploy-to-prod') {
            steps{
                echo 'Deploying to a production...'
            }
        }

        stage ('tests-on-prod') {
            steps{
                echo 'Running tests on production...'
            }
        }
    }
}
