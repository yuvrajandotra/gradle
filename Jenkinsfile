pipeline {
    agent any  // Use any available agent

    tools {
        gradle 'Gradle'  // This name must match the one configured under Jenkins > Global Tool Configuration
        jdk 'JDK'        // Same here for JDK
    }

    environment {
        PATH = "${tool 'Gradle'}/bin:${PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/yuvrajandotra/gradle.git'
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
