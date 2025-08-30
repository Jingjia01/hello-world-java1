pipeline {
    agent any
    tools {
        jdk 'Java17'   // The name you gave in Jenkins tool config
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Jingjia01/hello-world-java1.git'
            }
        }
        stage('Build') {
            steps { bat 'gradlew clean build'}
        }
        stage('Test') {
            steps { bat 'gradlew test'}
        }
        stage('Deploy') {
            steps { powershell 'java -jar build/libs/hello-world-java-V1.jar'}           
        }    
}

post {
        always {
            echo 'Cleaning up workspace'
            deleteDir() // Clean up the workspace after the build
        }
        success {
            echo 'Build succeeded!!!'
            // You could add notification steps here
        }
        failure {
            echo 'Build failed!'
            // You could add notification steps here
        }
    }
}
