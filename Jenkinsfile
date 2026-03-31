pipeline {
    agent any

    stages {
        stage ('install-pip-deps') {
            steps {
                echo 'Installing all required dependencies...'
                bat 'if exist python-greetings rmdir /s /q python-greetings'
                bat 'git clone https://github.com/mtararujs/python-greetings.git'
                bat 'dir python-greetings'
                bat 'cd python-greetings'
                bat 'python3 -m venv venv'

                // !!! + Veikt Python virtualizētas vides izveidi un izsaukt komandu nepieciešamo bibliotēku/pakotņu instalācijai pret virtualizēto vidi
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


// def deploy(String environment){
//     echo ""
// }



// def deploy(String environment){
//     echo "Deployment to ${environment} environment has started.."
//     sh "docker pull mtararujs/sample-book-app"
//     sh "docker compose stop sample-book-app-${environment}"
//     sh "docker compose rm sample-book-app-${environment}"
//     sh "docker compose up -d sample-book-app-${environment}"
//     echo "Deployment to ${environment} environment finished.."
// }