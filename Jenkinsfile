pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Run kubectl apply') {
            steps {
                sh 'minikube kubectl -- apply -f config-server.yml'
            }
        }
    }
}
