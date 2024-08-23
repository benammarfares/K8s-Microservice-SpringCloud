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
              kubernetesDeploy(configs: "config-server.yaml")
            }
          }
        }
    }
}
