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
                withKubeConfig(credentialsId: 'mykubeconfig') {
                    sh 'kubectl apply -f config-server.yml'
                }
            }
        }
    }
}
