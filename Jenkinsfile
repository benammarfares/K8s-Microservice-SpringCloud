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
                withKubeConfig(credentialsId: 'mykubeconfig') {
                    sh 'kubectl port-forward service/eureka-lb 31744:80'
                    sh 'sleep 5'

                }
            }
        }
        stage('Exposing Gateway') {
            steps {
                withKubeConfig(credentialsId: 'mykubeconfig') {
                sh 'kubectl port-forward service/cloud-gateway-svc 30950:80'
                sh 'sleep 5'
                sh '''
                curl -m 5 http://localhost:31744 || echo "Failed to reach Eureka service"
                '''
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