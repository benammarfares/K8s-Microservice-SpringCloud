pipeline {
    options {
        skipDefaultCheckout true
    }
      agent any
    tools {
      maven "3.9.8"
    }
    environment {
        CUSTOM_WORKSPACE = "/var/jenkins_home/workspace/testingMInikube@2"
    }
    stages {
        stage('Build Config Server') {
        agent any
            steps {
                checkout scm
                script {
                    sh "pwd"
                    sh "ls -la"
                    dir("cloud-config-server") {
                    withSonarQubeEnv('sonarserver') {
                        sh 'mvn sonar:sonar'
                    }
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }


        stage('Push Config Docker Image') {
          steps {
            script {
                sh "pwd"
                sh "ls -la"
                dir("${CUSTOM_WORKSPACE}/cloud-config-server") {
                    sh 'docker build -t fares121/cloud-config-server:1.0.0 .'
                      withCredentials([string(credentialsId: 'Docker', variable: 'docker_password')]) {
                        sh 'docker login -u fares121 -p ${docker_password}'
                        sh 'docker push fares121/cloud-config-server:1.0.0'
                      }
                }
            }
          }
        }


        stage('Build Service Registry Service') {
        agent any
            steps {
                checkout scm
                script {
                    sh "pwd"
                    sh "ls -la"
                    dir("service-registry") {
                    withSonarQubeEnv('sonarserver') {
                        sh 'mvn sonar:sonar'
                    }
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Push Service Registry Docker Image') {
          steps {
            script {
                sh "pwd"
                sh "ls -la"
                dir("${CUSTOM_WORKSPACE}/service-registry") {
                    sh 'docker build -t fares121/service-registry:1.0.0 .'
                      withCredentials([string(credentialsId: 'Docker', variable: 'docker_password')]) {
                        sh 'docker login -u fares121 -p ${docker_password}'
                        sh 'docker push fares121/service-registry:1.0.0'
                      }
                }
            }
          }
        }


        stage('Build cloud-gateway Service') {
        agent any
            steps {
                checkout scm
                script {
                    sh "pwd"
                    sh "ls -la"
                    dir("cloud-gateway") {
                    withSonarQubeEnv('sonarserver') {
                        sh 'mvn sonar:sonar'
                    }
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Push cloud-gateway Docker Image') {
          steps {
            script {
                sh "pwd"
                sh "ls -la"
                dir("${CUSTOM_WORKSPACE}/cloud-gateway") {
                    sh 'docker build -t fares121/cloud-gateway:1.0.0 .'
                      withCredentials([string(credentialsId: 'Docker', variable: 'docker_password')]) {
                        sh 'docker login -u fares121 -p ${docker_password}'
                        sh 'docker push fares121/cloud-gateway:1.0.0'
                      }
                }
            }
          }
        }

        stage('Build assurance Service') {
        agent any
            steps {
                checkout scm
                script {
                    sh "pwd"
                    sh "ls -la"
                    dir("assurance") {
                    withSonarQubeEnv('sonarserver') {
                        sh 'mvn sonar:sonar'
                    }
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Push assurance Docker Image') {
          steps {
            script {
                sh "pwd"
                sh "ls -la"
                dir("${CUSTOM_WORKSPACE}/assurance") {
                    sh 'docker build -t fares121/assurance-service:1.0.0 .'
                      withCredentials([string(credentialsId: 'Docker', variable: 'docker_password')]) {
                        sh 'docker login -u fares121 -p ${docker_password}'
                        sh 'docker push fares121/assurance-service:1.0.0'
                      }
                }
            }
          }
        }

        stage('Build assurancePolicy Service') {
        agent any
            steps {
                checkout scm
                script {
                    sh "pwd"
                    sh "ls -la"
                    dir("assurancePolicy") {
                    withSonarQubeEnv('sonarserver') {
                        sh 'mvn sonar:sonar'
                    }
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Push assurancePolicy Docker Image') {
          steps {
            script {
                sh "pwd"
                sh "ls -la"
                dir("${CUSTOM_WORKSPACE}/assurancePolicy") {
                    sh 'docker build -t fares121/assurancepolicy-service:1.0.0 .'
                      withCredentials([string(credentialsId: 'Docker', variable: 'docker_password')]) {
                        sh 'docker login -u fares121 -p ${docker_password}'
                        sh 'docker push fares121/assurancepolicy-service:1.0.0'
                      }
                }
            }
          }
        }


        stage('Build department-service Service') {
        agent any
            steps {
                checkout scm
                script {
                    sh "pwd"
                    sh "ls -la"
                    dir("department-service") {
                    withSonarQubeEnv('sonarserver') {
                        sh 'mvn sonar:sonar'
                    }
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Push department-service Docker Image') {
          steps {
            script {
                sh "pwd"
                sh "ls -la"
                dir("${CUSTOM_WORKSPACE}/department-service") {
                    sh 'docker build -t fares121/department-service:1.0.0 .'
                      withCredentials([string(credentialsId: 'Docker', variable: 'docker_password')]) {
                        sh 'docker login -u fares121 -p ${docker_password}'
                        sh 'docker push fares121/department-service:1.0.0'
                      }
                }
            }
          }
        }



        stage('Build user-service Service') {
        agent any
            steps {
                checkout scm
                script {
                    sh "pwd"
                    sh "ls -la"
                    dir("user-service") {
                    withSonarQubeEnv('sonarserver') {
                        sh 'mvn sonar:sonar'
                    }
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Push user-service Docker Image') {
          steps {
            script {
                sh "pwd"
                sh "ls -la"
                dir("${CUSTOM_WORKSPACE}/user-service") {
                    sh 'docker build -t fares121/user-service:1.0.0 .'
                      withCredentials([string(credentialsId: 'Docker', variable: 'docker_password')]) {
                        sh 'docker login -u fares121 -p ${docker_password}'
                        sh 'docker push fares121/user-service:1.0.0'
                      }
                }
            }
          }
        }


        stage('Checkout to the kubernetes github repo') {
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
                        sh '''
                        kubectl port-forward service/eureka-lb 31744:80 &
                        echo $! > eureka-lb.pid
                        '''
                        sh 'sleep 5'
                }
            }
        }

        stage('Exposing Gateway') {
            steps {
                withKubeConfig(credentialsId: 'mykubeconfig') {
                sh '''
                kubectl port-forward service/cloud-gateway-svc 30950:80 &
                echo $! > cloud-gateway-svc.pid
                '''
                sh 'sleep 5'
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


