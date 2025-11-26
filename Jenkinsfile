pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/advika16/devops-sample-code.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo 'Installing dependencies...'
                sh '''
                    python3 --version
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh '''
                    . venv/bin/activate
                    python -m pytest
                '''
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t advika-python-app .'
            }
        }

        stage('Docker Run') {
            steps {
                echo 'Running Docker container...'
                sh 'docker run -d -p 5000:5000 --name python-app-container advika-python-app || true'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline Failed. Check Logs!'
        }
        success {
            echo 'Pipeline Completed Successfully!'
        }
    }
}
