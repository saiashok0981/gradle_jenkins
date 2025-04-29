pipeline {
    agent any

    tools {
        gradle 'Gradle'   // Ensure this name matches what's configured in Jenkins tools
        jdk 'JDK'      // Ensure this matches a JDK 11 installation in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/saiashok0981/gradle_jenkins.git'
            }
        }

        stage('Build') {
            steps {
                sh 'gradle clean build'
            }
        }

        stage('Test') {
            steps {
                sh 'gradle test'
            }
        }

        stage('Run Application') {
            steps {
                
                    sh 'gradle run'
                
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
