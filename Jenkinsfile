pipeline {
    agent any

    stages {
        stage ('install-pip-deps') {
            echo "Installing all required dependencies..."
        }
        
        stage ('deploy-to-dev') {
            echo "Deploying to a development..."
        }

        stage ('tests-on-dev') {
            echo "Running tests on development..."
        }

        stage ('deploy-to-stg') {
            echo "Deploying to a staging..."
        }

        stage ('tests-on-stg') {
            echo "Running tests on staging..."
        }

        stage ('deploy-to-preprod') {
            echo "Deploying to a preprod..."
        }

        stage ('tests-on-preprod') {
            echo "Running tests on preprod..."
        }

        stage ('deploy-to-prod') {
            echo "Deploying to a production..."
        }

        stage ('tests-on-prod') {
            echo "Running tests on production..."
        }
    }
}
