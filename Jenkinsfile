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
                        sh 'kubectl get all'
                        sh 'kubectl apply -f ./'
                        sh 'kubectl get all'
                    }
            }
        }
        stage('Exposing Eureka Cloud Service') {
            steps {
                sh 'kubectl port-forward service/eureka-lb 8761:80'
                sh 'sleep 5'

            }
        }
        stage('Exposing Gateway') {
            steps {
                sh 'kubectl port-forward service/cloud-gateway-svc 30950:80'
                sh 'sleep 5'

            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}