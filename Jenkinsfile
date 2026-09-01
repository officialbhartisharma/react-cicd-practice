pipeline {
    agent any

    environment {
        NETLIFY_SITE_ID = 'c76497db-a4ee-4a9b-836c-5ad42af39aeb'
    }

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

        stage('Deploy') {
            steps {
                withCredentials([
                    string(
                        credentialsId: 'netlify-token-new',
                        variable: 'NETLIFY_AUTH_TOKEN'
                    )
                ]) {
                    sh 'netlify deploy --prod --dir=dist --site=$NETLIFY_SITE_ID'
                }
            }
        }

    }
}