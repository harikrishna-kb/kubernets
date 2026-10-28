pipeline {
    agent any
    environment {
        DOCKER_USERNAME = "saharsh1211"
        IMAGE_NAME = "online-book-store"
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
                bat 'kubectl rollout status deployment/online-book-store'
                bat 'kubectl get pods -l app=online-book-store'
                bat 'kubectl get svc online-book-store-service'
            }
        }
    }
}
