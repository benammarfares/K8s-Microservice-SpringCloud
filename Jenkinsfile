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
                            echo " changes in assurance directory."
                        } else {
                            echo "No changes in assurance directory. Skipping build."
                        }
                    }
                }
            }
        }


    }
}

def handleJarComparison() {
    def oldJarPath = '/var/jenkins_home/workspace/k8s-cloud@2/assurance/target/assurance.jar'
    def newJarPath = '/var/jenkins_home/workspace/k8s-cloud@2/assurance/target/assurance.jar'

    if (fileExists(oldJarPath)) {
        sh "cp ${oldJarPath} ${oldJarPath}.backup"
    }

    sh "mvn clean package -DskipTests"

    def newJarFile = "${newJarPath}/your-app.jar"  // Update with your actual JAR path

    if (fileExists("${oldJarPath}.backup")) {
        def isDifferent = sh(script: "cmp -s ${oldJarPath}.backup ${newJarFile} || echo 'different'", returnStdout: true).trim()
        return isDifferent.contains('different')
    } else {
        return true
    }
}