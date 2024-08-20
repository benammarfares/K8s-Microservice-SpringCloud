pipeline {
    options {
        skipDefaultCheckout true
    }
      agent any
    tools {
      maven "3.9.8"
    }
    stages {
        stage('Build Config Server') {
        agent any
            steps {
                checkout scm
                script {
                    sh "pwd"
                    sh "ls -la"
                    dir("configServer") {
                      sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }
    }
}