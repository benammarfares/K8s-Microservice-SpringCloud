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
                 checkout scm
                script {
                dir("assurance") {
                def assuranceChanged = changesInDirectory('assurance')
                    if (assuranceChanged) {
                        sh 'mvn clean package -DskipTests'
                    }
                    else {
                        echo "No changes in assurance directory. Skipping build."
                    }
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