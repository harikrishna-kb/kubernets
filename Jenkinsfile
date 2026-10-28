pipeline {
    agent any
    environment {
        DOCKER_USERNAME = "harikrishna7416"
        IMAGE_NAME = "agile-kubernetes"
        IMAGE_TAG = "latest"
    }
    stages {
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
            }
        }
        stage('Verify Rollout') {
            steps {
                bat 'kubectl rollout status deployment/agile-kubernetes'
                bat 'kubectl get pods -l app=agile-kubernetes'
                bat 'kubectl get svc agile-kubernetes-service'
            }
        }
    }
}
