pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps { git 'https://github.com/your-repo.git' }
    }

    stage('Build') {
      steps { sh 'mvn clean package' }
    }

    stage('Docker Build') {
      steps {
        sh 'docker build -t cicd-app .'
      }
    }

    stage('Push to ECR') {
      steps {
        sh '''
        aws ecr get-login-password | docker login --username AWS --password-stdin <ECR_URI>
        docker tag cicd-app:latest <ECR_URI>:latest
        docker push <ECR_URI>:latest
        '''
      }
    }

    stage('Deploy to Kubernetes') {
      steps {
        sh 'kubectl apply -f k8s/'
      }
    }
  }
}
