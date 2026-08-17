pipeline {

    agent any

    stages {

        stage('Create Virtual Environment') {
            steps {
                echo 'Creating Python virtual environment...'

                sh '''
                    python3 -m venv .venv
                    .venv/bin/python --version
                    .venv/bin/pip --version
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing Python dependencies...'

                sh '''
                    .venv/bin/pip install --upgrade pip
                    .venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Build') {
            steps {
                echo '========== BUILD STAGE =========='
                echo 'Building the application...'

                sh '''
                    .venv/bin/python -m compileall .
                '''
            }
        }

        stage('Test') {
            steps {
                echo '========== TEST STAGE =========='
                echo 'Running automated tests...'

                sh '''
                    .venv/bin/python -m pytest -v
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '========== DEPLOY STAGE =========='
                echo 'Deploying application...'

                sh '''
                    echo "Application deployed successfully!"
                '''
            }
        }
    }

    post {

        success {
            echo '================================='
            echo 'Pipeline completed successfully!'
            echo '================================='
        }

        failure {
            echo 'Pipeline failed!'
        }

        always {
            echo 'Pipeline execution completed.'
        }
    }
}