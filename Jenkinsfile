pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        withCredentials([[
          $class: 'AmazonWebServicesCredentialsBinding',
          accessKeyVariable: 'AWS_ACCESS_KEY_ID',
          secretKeyVariable: 'AWS_SECRET_ACCESS_KEY',
          credentialsId: 'my-aws-iam-credential'
        ]]) {
          sh 'echo "Hello, world!"'
        }
      }
    }
  }
}
