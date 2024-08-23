pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'minikube', contextName: 'minikube', credentialsId: 'minikube-jenkins-secret', namespace: '', restrictKubeConfigAccess: false, serverUrl: 'https://192.168.49.2:8443') {
                        sh "kubectl get ns"
                }
            }
        }
    }
}