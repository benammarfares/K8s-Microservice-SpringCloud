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
            when {
                expression {
                    // Check if the assurancePolicy directory has changes
                    def changes = currentBuild.changeSets.collect { it.items }.flatten()
                    def changedPaths = changes.collect { it.paths }
                    def assurancePolicyChanged = changedPaths.flatten().any { it.startsWith('assurancePolicy/') }
                    assurancePolicyChanged
                }
            }
            steps {
                checkout scm
                dir("assurancePolicy") {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }

        stage('Build assurancePolicy Docker Image') {
            when {
                expression {
                    // Only execute this stage if assurancePolicy has changed
                    def changes = currentBuild.changeSets.collect { it.items }.flatten()
                    def changedPaths = changes.collect { it.paths }
                    def assurancePolicyChanged = changedPaths.flatten().any { it.startsWith('assurancePolicy/') }
                    assurancePolicyChanged
                }
            }
            steps {
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
}