pipeline {
  agent any
  environment {
    AWS_DEFAULT_REGION = 'us-west-2'
  }
  stages {
    stage('deploy') {
      steps {
        withCredentials([[
          $class: 'AmazonWebServicesCredentialsBinding',
          accessKeyVariable: 'AWS_ACCESS_KEY_ID',
          credentialsId: 'my-aws-iam-credential',
          secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
        ]]) {
          sh "aws configure set region $AWS_DEFAULT_REGION"
          sh "aws s3 cp Code/index.html s3://my-static-bucket-jenkins1"
        }
      }
    }
  }
}
