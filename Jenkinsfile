pipeline {

    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building the application...'

                sh 'python3 --version'
                sh 'python3 app.py'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'

                sh 'python3 -m pip install --user -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests...'

                sh 'python3 -m pytest -v'
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
