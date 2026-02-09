pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/maheshwarishivanandswami/github-actions-cicd-example.git'
            }
        }

        stage('Setup Python') {
            steps {
                sh '''
                python3 --version
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                pip install -e .
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                . venv/bin/activate
                python -m unittest discover
                '''
            }
        }
    }

    post {
        success {
            echo 'BUILD SUCCESSFUL 🎉'
        }
        failure {
            echo 'BUILD FAILED ❌'
        }
    }
}
