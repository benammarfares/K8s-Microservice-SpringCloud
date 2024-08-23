pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '', contextName: '', credentialsId: 'mykubeconfig', namespace: '', serverUrl: '']]) {
                        sh "kubectl get nodes"
                }
            }
        }
    }
}