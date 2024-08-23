pipeline {
    agent any
    stages {
        stage('Run kubectl get all') {
            steps {
                sh 'alias kubectl="minikube kubectl --"'
                sh 'kubectl apply -f config-server.yml'
                sh 'kubectl get all'
            }
        }
    }
}