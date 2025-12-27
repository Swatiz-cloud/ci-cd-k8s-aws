pipeline {
    agent any

    environment {
        ECR_REPO = "<AWS_ECR_URI>"
        AWS_REGION = "ap-south-1"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/Swatiz-cloud/ci-cd-k8s-aws.git'
            }
        }

        stage('Build Application') {
            steps {
                sh 'cd app && mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'cd app && docker build -t cicd-app .'
            }
        }

        stage('Push to AWS ECR') {
            steps {
                sh '''
                aws ecr get-login-password --region $AWS_REGION \
                | docker login --username AWS --password-stdin $ECR_REPO

                docker tag cicd-app:latest $ECR_REPO:latest
                docker push $ECR_REPO:latest
                '''
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                kubectl apply -f k8s/namespace.yml
                kubectl apply -f k8s/
                '''
            }
        }
    }
}
