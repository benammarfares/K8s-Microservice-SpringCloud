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
                    def changedFiles = sh(script: 'git log -2 --name-only --oneline --pretty="format:"', returnStdout: true).trim()
                    if (changedFiles ==~ "(.*)dir1(.*)|(.*)dir2(.*)|(.*)somefile") {
                        echo "Changes detected in relevant files. Proceeding with the build."
                    } else {
                        echo "No relevant changes detected. Skipping the build."
                    }
                }
            }
        }
        stage('Build Assurance Service') {
            when {
                expression { changedFiles() }
            }
            steps {
                checkout scm
                dir("assurance") {
                    // Your existing build steps for Assurance Service
                }
            }
        }
        // Add other stages as needed
    }
}

def changedFiles() {
    def changeSet = sh(script: 'git log -2 --name-only --oneline --pretty="format:"', returnStdout: true).trim()
    return (changeSet ==~ "(.*)dir1(.*)|(.*)dir2(.*)|(.*)somefile")
}
