pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-east-1'
        AWS_ACCESS_KEY_ID = credentials('aws-iam-user-access-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-iam-user-secret-access-key')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                sh "aws s3 sync dist/ s3://my-bucket-name --delete"
            }
        }
    }
}
