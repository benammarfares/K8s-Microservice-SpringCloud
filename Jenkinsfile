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

        stage('Build Assurance Service') {
            steps {
                checkout scm
                script {
                    dir("assurance") {
                        def assuranceChanged = changesInDirectory('assurance')
                        if (assuranceChanged) {
                            sh 'mvn clean package -DskipTests'
                        } else {
                            echo "No changes in assurance directory. Skipping build."
                        }
                    }
                }
            }
        }


    }
}

def changesInDirectory(String dir) {
    // Ensure the repository is up to date
    sh "git fetch origin"

    // Compare the local assurance directory against the remote
    def output = sh(script: "git diff --name-only HEAD origin/main -- ${dir}", returnStdout: true).trim()

    // Check for changes in the specified directory
    def changes = output.split('\n').findAll { it.startsWith(dir) }

    return changes.size() > 0
}