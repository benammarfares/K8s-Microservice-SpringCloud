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

        stage('Build assurance Service') {
            steps {
                script {
                    def assuranceChanged = changesInDirectory('assurance')
                    if (assuranceChanged) {
                        checkout scm
                        dir("assurance") {
                            sh 'mvn clean package -DskipTests'
                        }
                    } else {
                        echo "No changes in assurance directory. Skipping build."
                    }
                }
            }
        }

        stage('Build assurance Docker Image') {
            steps {
                script {
                    def assuranceChanged = changesInDirectory('assurance')
                    if (assuranceChanged) {
                        dir("${CUSTOM_WORKSPACE}/assurance") {
                            sh 'docker build -t fares121/assurance-service:1.0.0 .'
                            withCredentials([string(credentialsId: 'Docker', variable: 'docker_password')]) {
                                sh 'docker login -u fares121 -p ${docker_password}'
                                sh 'docker push fares121/assurance-service:1.0.0'
                            }
                        }
                    } else {
                        echo "No changes in assurance directory. Skipping Docker image build."
                    }
                }
            }
        }
    }
}

def changesInDirectory(directory) {
    def changes = currentBuild.changeSets.collect { it.items }.flatten()
    def changedPaths = changes.collect { it.paths }
    changedPaths.flatten().any { it.startsWith("${directory}/") }
}