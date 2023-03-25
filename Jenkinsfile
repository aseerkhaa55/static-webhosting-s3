pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID = credentials('AKIA3PRXSPHJORD3UV6F')
        AWS_SECRET_ACCESS_KEY = credentials('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')
        AWS_DEFAULT_REGION = 'us-east-1'
        S3_BUCKET_NAME = 'my-static-bucket-jenkins1'
        WEBSITE_DIRECTORY = 'public'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Deploy to S3') {
            steps {
                sh "aws s3 sync ${env.WEBSITE_DIRECTORY} s3://${env.S3_BUCKET_NAME} --delete"
            }
        }
    }
}
