pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                cleanWs()
                git branch: 'main',
                    url: 'https://github.com/benammarfares/Kubernetes-yml-for-service-deploy.git'
                sh 'ls -la'
                sh 'git rev-parse HEAD'
                    withKubeConfig(credentialsId: 'mykubeconfig') {
                        sh 'kubectl delete -f ./'
                        sh 'kubectl get all'
                        sh 'kubectl apply -f ./'
                        sh 'minikube service eureka-lb'
                    }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}