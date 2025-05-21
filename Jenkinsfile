pipeline {
    agent any

    tools {
        gradle 'gradle'  // Ensure this matches Jenkins config
        jdk 'JDK'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/yuvrajandotra/gradle.git'
            }
        }

        stage('Build') {
            steps {
                sh './gradlew clean build'  // Modern Gradle build command
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'  // Run unit tests
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
