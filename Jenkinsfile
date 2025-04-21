pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/AndySee04/practical_8_github_actions.git'
            }
        }
        stage('Build') {
            steps {
                // powershell 'gradle clean build'
                bat 'gradle build'
            }
        }
        stage('Test') {
            steps {
                // powershell 'gradle test'
                bat 'gradle test'
            }
        }
        stage('Deploy') {
            steps {
                bat 'java -jar build/libs/p8.jar'
            }
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
