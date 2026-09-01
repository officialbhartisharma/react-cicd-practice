pipeline {
    agent any

    stages {
        
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/officialbhartisharma/react-cicd-practice.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Lint') {
            steps {
                sh 'npm run lint'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

    }
}