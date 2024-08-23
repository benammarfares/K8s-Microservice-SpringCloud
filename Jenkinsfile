pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                withKubeConfig(credentialsId: 'mykubeconfig') {
                    sh 'kubectl get all'
                    sh 'kubectl apply -f config-server.yml'
                }
            }
        }
    }
}