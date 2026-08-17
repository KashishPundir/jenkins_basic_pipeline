pipeline {

    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building the application...'

                sh 'python --version'
                sh 'python app.py'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'

                sh 'python -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests...'

                sh 'python -m pytest -v'
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
    }
}