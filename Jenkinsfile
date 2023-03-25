pipeline {
  agent any
  stages {
    stage('deploy') {
      steps {
        withCredentials([[
          $class: 'AmazonWebServicesCredentialsBinding',
          accessKeyVariable: 'AWS_ACCESS_KEY_ID',
          secretKeyVariable: 'AWS_SECRET_ACCESS_KEY',
          credentialsId: 'my-aws-iam-credential'
        ]]) {
          sh "aws s3 cp Code/index.html s3://my-static-bucket-jenkins1"
        }
      }
    }
  }
}
