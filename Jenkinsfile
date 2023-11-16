pipeline {
  agent any
  stages {
    stage('aws-ecr-login') {
      steps {
        withEnv(overrides: ["AWS_ACCESS_KEY_ID=${env.AWS_ACCESS_KEY_ID}", "AWS_SECRET_ACCESS_KEY=${env.AWS_SECRET_ACCESS_KEY}", "AWS_DEFAULT_REGION=${env.AWS_DEFAULT_REGION}"]) {
          sh 'printenv'
          sh 'aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/a0i7l2w3'
          sh 'docker build -t femi.project .'
          sh 'docker tag femi.project:latest public.ecr.aws/a0i7l2w3/femi.project:latest'
          sh 'docker push public.ecr.aws/a0i7l2w3/femi.project:latest'
        }

      }
    }

    stage('ssh') {
      steps {
        sh '''sshagent([\'server1\']) {
    sh "ssh -tt -o StrictHostKeyChecking=no ubuntu@54.75.23.241"
}
 '''
        }
      }

    }
  }