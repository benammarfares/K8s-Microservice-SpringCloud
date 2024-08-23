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
              deployKubeConfig(configs: "config-server.yaml")
            }
          }
        }
    }
}
