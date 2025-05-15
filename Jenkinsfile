pipeline {
    agent any

    tools {
        gradle 'Gradle'   // Must match the name in Jenkins Tool Config
        jdk 'JDK'         // Must match the JDK name
    }

    environment {
        GRADLE_HOME = tool 'Gradle'
        PATH = "${GRADLE_HOME}/bin:${env.PATH}"
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
