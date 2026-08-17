pipeline {

    agent any

    stages {

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
    }
}