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
    // Get the output of the status command to check if there are uncommitted changes
    def output = sh(script: "git status --porcelain", returnStdout: true).trim()

    // Check for changes in the specified directory
    def changes = output.split('\n').findAll { line ->
        line.startsWith(' M') || line.startsWith('A ') // Check for modified (M) or added (A) files
    }.collect { line ->
        // Extract the file path from the status line
        line.substring(3).trim() // Remove status prefix
    }.findAll { file ->
        file.startsWith(dir)
    }

    return changes.size() > 0
}