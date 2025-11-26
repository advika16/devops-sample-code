pipeline {
    agent {
        docker { image 'python:3.10' }
    }

    stages {
        stage('Build') {
            steps {
                echo "Creating virtual environment and installing dependencies..."
                sh 'python -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo "Running Tests..."
                sh '. venv/bin/activate && python -m pytest'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploy step executed."
            }
        }
    }

    post {
        failure {
            echo "Pipeline failed. Check logs for details."
        }
    }
}
