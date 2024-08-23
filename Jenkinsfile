pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Run kubectl apply') {
            withKubeConfig(credentialsId: 'mykubeconfig') {
                sh 'kubectl apply -f config-server.yml'
            }
        }
    }
}
