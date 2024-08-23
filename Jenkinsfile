pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Deploying React.js container to Kubernetes') {
          steps {
            script {
              kubeconfig(credentialsId: 'mykubeconfig', serverUrl: 'https://192.168.49.2:8443') {
                echo 'Deploying React.js container to Kubernetes'
              }
            }
          }
        }
    }
}
