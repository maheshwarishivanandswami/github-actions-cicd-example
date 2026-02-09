pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/maheshwarishivanandswami/github-actions-cicd-example.git'
            }
        }

        stage('Setup Python') {
            steps {
                sh '''
                python3 --version
                pip3 --version
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                pip3 install --upgrade pip
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
