pipeline {
    agent any

    tools {
        gradle 'Gradle'   // Ensure this name matches what's configured in Jenkins tools
        jdk 'JDK 11'      // Ensure this matches a JDK 11 installation in Jenkins
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
                sh './gradlew clean build'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }

        stage('Run Application') {
            steps {
                timeout(time: 2, unit: 'MINUTES') {
                    sh './gradlew run'
                }
            }
        }
    }

    post {
        success {
            echo '✅ Build and deployment successful!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
