pipeline {
    agent any

    tools {
        gradle 'Gradle'  // Ensure this matches your Jenkins Gradle tool name
        jdk 'JDK'        // Ensure this matches your Jenkins JDK tool name
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/saiashok0981/gradle_jenkins.git'
            }
        }

        stage('Set Permissions') {
            steps {
                sh 'chmod +x gradlew'
            }
        }

        stage('Build') {
            steps {
                sh './gradlew build'  // Use the Gradle wrapper
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }

        stage('Run Application') {
            steps {
                sh './gradlew run'
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
