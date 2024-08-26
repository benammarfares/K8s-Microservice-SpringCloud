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



        stage('Build assurance Service') {
        agent any
            steps {
                checkout scm
                script {
                    sh "pwd"
                    sh "ls -la"
                    dir("assurance") {
                    sh 'mvn compiler:compile'
                    withSonarQubeEnv('sonarserver') {
                        sh 'mvn sonar:sonar'
                    }
                      sh 'mvn clean package -DskipTests'
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










    }

}


