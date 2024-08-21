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
        OLD_JAR_PATH = "/var/jenkins_home/workspace/k8s-cloud/assurance/target/assurance.jar"
        NEW_JAR_FILE = "/var/jenkins_home/workspace/k8s-cloud/assurance/target/assurance.jar"
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
    def backupJarPath = '/var/jenkins_home/workspace/k8s-cloud/assurance/target/assuranceBackup.jar'  // New backup path
     sh "cp ${oldJarPath} ${backupJarPath}"
     sh "mvn clean package -DskipTests"

    def isDifferent = sh(script: "cmp -s ${backupJarPath} ${newJarFile} || echo 'different'", returnStdout: true).trim()

    // Step 4: Check for differences
    if (isDifferent.contains('different')) {
        echo "Jar files are different"
        return true
    } else {
        echo "Jar files are the same"
        return false
    }
}