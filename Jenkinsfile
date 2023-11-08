pipeline {
  agent any
  stages {
    stage('aws-ecr-login') {
      steps {
        withEnv(overrides: ["AWS_ACCESS_KEY_ID=${env.AWS_ACCESS_KEY_ID}", "AWS_SECRET_ACCESS_KEY=${env.AWS_SECRET_ACCESS_KEY}", "AWS_DEFAULT_REGION=${env.AWS_DEFAULT_REGION}"]) {
          sh 'printenv'
          sh 'docker login --username AWS -p  $(aws ecr-public get-login-password --region us-east-1) public.ecr.aws/a0i7l2w3 '
         
        }

      }
    }

  }
}
