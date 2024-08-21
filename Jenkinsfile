def changedFiles = sh(script: 'git log -2 --name-only --oneline --pretty="format:"', returnStdout: true).trim()

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
        stage('Check Changes') {
            steps {
                script {
                    echo "Changed files: ${changedFiles}"
                    if (changedFiles ==~ "(.*)assurance(.*)") {
                        echo "Changes detected in relevant files. Proceeding with the build."
                    } else {
                        echo "No relevant changes detected. Skipping the build."
                    }
                }
            }
        }
        stage('Build Assurance Service') {
            when {
                expression { changedFiles }
            }
            steps {
                checkout scm
                dir("assurance") {
                    // Additional steps for building the assurance service
                }
            }
        }
    }
}
