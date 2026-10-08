pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'thilak0402/college-notice-board:latest'
        CRED_ID = 'dockerhub-creds'
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Thilak0402/College_Notice_Board.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${env.DOCKER_IMAGE}")
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', "${env.CRED_ID}") {
                        dockerImage.push();
                    }
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                bat 'set KUBECONFIG=C:\\Users\\batch1\\.kube\\config && kubectl apply -f deployment.yaml --validate=false'
            }
        }
    }
}