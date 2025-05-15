pipeline {
    agent any

    tools {
        gradle 'Gradle'
        jdk 'JDK'
    }

    environment {
        PATH = "${tool 'Gradle'}/bin:${PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/yuvrajandotra/gradle.git'
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
