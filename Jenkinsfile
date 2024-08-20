pipeline {
    options {
        skipDefaultCheckout true
    }
      agent any
    tools {
      maven "3.9.8"
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
                dir("cloud-config-server") {
                    sh 'docker build -t fares121\cloud-config-server:1.0.0 .'
                      withCredentials([string(credentialsId: 'Docker', variable: 'docker_password')]) {
                        sh 'docker login -u fares121 -p ${docker_password}'
                        sh 'docker push fares121\cloud-config-server:1.0.0'
                      }
                }
            }
          }
        }



    }
}