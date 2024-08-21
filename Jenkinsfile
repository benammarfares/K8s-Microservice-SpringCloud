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
        OLD_JAR_PATH = "/var/jenkins_home/workspace/k8s-cloud/assurance/target"
        NEW_JAR_FILE = "/var/jenkins_home/workspace/k8s-cloud/assurance/target"
    }
    stages {

        stage('Build Assurance Service') {
            steps {
                checkout scm
                script {
                    dir("assurance") {
                        def assuranceChanged = handleJarComparison(OLD_JAR_PATH, NEW_JAR_FILE)

                    }
                }
            }
        }


    }
}

def handleJarComparison(String oldJarPath, String newJarFile) {
    // Create a backup of the old JAR
    if (fileExists("${oldJarPath}/assurance.jar")) {
        sh "cp ${oldJarPath}/assurance.jar ${oldJarPath}/assuranceBackup.jar"
    } else {
        echo "Old JAR does not exist, skipping backup."
    }

    // Build the new JAR
    sh "mvn clean package -DskipTests"

    // Compare the old JAR backup with the newly built JAR
    def isDifferent = sh(script: "cmp -s ${oldJarPath}/assuranceBackup.jar ${newJarFile}/assurance.jar || echo 'different'", returnStdout: true).trim()

    // Check for differences
    if (isDifferent.contains('different')) {
        echo "Jar files are different"
        return true
    } else {
        echo "Jar files are the same"
        return false
    }
}