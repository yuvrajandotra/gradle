pipeline {
    agent any

    tools {
        gradle 'gradle' // Name must match Jenkins Maven installation name
        jdk 'JDK'     // Name must match Jenkins JDK installation
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/yuvrajandotra/gradle.git'
            }
        }

        stage('Build') {
            steps {
                sh 'gradle build'
            }
        }

        stage('Test') {
            steps {
                sh 'gradle test'
            }
        }

        stage('Run Application') {
            steps {
                sh 'gradle run' // Replace with your main class
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
