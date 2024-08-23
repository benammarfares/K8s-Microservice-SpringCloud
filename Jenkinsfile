pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Run kubectl get all') {
            steps {
                sh 'minikube start'
            }
        }
    }
}