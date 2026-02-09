pipeline {
    agent {
        docker {
            image 'python:3.10-slim'
        }
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Python Version') {
            steps {
                sh 'python --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                pip install --upgrade pip
                pip install -r requirements.txt
                pip install -e .
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh 'python -m unittest discover'
            }
        }
    }

    post {
        success {
            echo 'BUILD SUCCESS ✅'
        }
        failure {
            echo 'BUILD FAILED ❌'
        }
    }
}
