pipeline {
    options {
        skipDefaultCheckout true
    }
      agent any
    tools {
      maven "3.9.8"
    }
    environment {
        CUSTOM_WORKSPACE = "/var/jenkins_home/workspace/k8s-cloud@2"
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
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }


        stage('Build Assurance Docker Image') {
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
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Build Service Registry Docker Image') {
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
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Build cloud-gateway Docker Image') {
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
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Build assurance Docker Image') {
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
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Build assurancePolicy Docker Image') {
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
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Build department-service Docker Image') {
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
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Build user-service Docker Image') {
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


    }
}