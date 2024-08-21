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
                        def assuranceChanged = handleJarComparison()
 
                    }
                }
            }
        }


    }
}

def handleJarComparison() {
    def oldJarPath = '/var/jenkins_home/workspace/k8s-cloud/assurance/target/assurance.jar'
    def newJarPath = '/var/jenkins_home/workspace/k8s-cloud/assurance/target/assurance.jar'

    if (fileExists(oldJarPath)) {
        sh "cp ${oldJarPath} ${oldJarPath}.backup"
    }

    sh "mvn clean package -DskipTests"

    def newJarFile = "${newJarPath}/assurance.jar"

        def isDifferent = sh(script: "cmp -s ${oldJarPath}.backup ${newJarFile} || echo 'different'", returnStdout: true).trim()
        return isDifferent.contains('different')

        if (isDifferent.contains('different')) {
            echo "Jar files are different"
            return true
        } else {
            echo "Jar files are same"
            return false
        }

}