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
                sh 'alias kubectl="minikube kubectl --"'
                sh 'kubectl apply -f config-server.yml'
            }
        }
    }
}