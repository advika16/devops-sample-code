pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Installing dependencies...'
                sh 'python3 --version || python --version'
                sh 'python3 -m venv venv || python -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh '. venv/bin/activate && python -m pytest'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy Stage Complete!'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline Failed. Check Logs!'
        }
        success {
            echo 'Pipeline Successful!'
        }
    }
}
