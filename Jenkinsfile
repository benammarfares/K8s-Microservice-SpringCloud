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
     echo "No changes in assurance directory. Skipping buildd."
    def changes = []
    def output = sh(script: "git diff --name-only HEAD^ HEAD", returnStdout: true).trim()
    output.split('\n').each { file ->
        if (file.startsWith(dir)) {
            changes.add(file)
        }
    }
    return changes.size() > 0
}