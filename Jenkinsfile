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
                python3 --version || apt update && apt install -y python3 python3-pip
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m pip install --upgrade pip
                pip3 install -r requirements.txt
                pip3 install -e .
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                python3 -m unittest discover
                '''
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
