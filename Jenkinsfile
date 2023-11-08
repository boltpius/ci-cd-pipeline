pipeline {
  agent any
  stages {
    stage('aws-ecr-login') {
      steps {
         withEnv(["AWS_ACCESS_KEY_ID=${env.AWS_ACCESS_KEY_ID}", "AWS_SECRET_ACCESS_KEY=${env.AWS_SECRET_ACCESS_KEY}", "AWS_DEFAULT_REGION=${env.AWS_DEFAULT_REGION}"]) { 
        sh 'docker login --username AWS --password-stdin  $(aws ecr-public get-login-password --region us-east-1) public.ecr.aws/a0i7l2w3 ' }
      }
    }

  }
}

// docker build -t femi.project .
// docker tag femi.project:latest public.ecr.aws/a0i7l2w3/femi.project:latest
// docker push public.ecr.aws/a0i7l2w3/femi.project:latest

