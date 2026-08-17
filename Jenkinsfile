pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub...'
                checkout scm
            }
        }

        stage('Check Python') {
            steps {
                echo 'Checking Python installation...'
                sh 'python3 --version'
                sh 'python3 -m pip --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Creating virtual environment and installing dependencies...'

                sh '''
                    python3 -m venv venv
                    ./venv/bin/python -m pip install --upgrade pip
                    ./venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'

                sh '''
                    ./venv/bin/python -m compileall .
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests...'

                sh '''
                    ./venv/bin/python -m pytest -v
                '''
            }
        }
    }

    post {

        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'CI/CD Pipeline failed!'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}