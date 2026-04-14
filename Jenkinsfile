pipeline {
    agent any

    tools {
        jdk 'JDK'
        // No need for gradle tool if using wrapper
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/numankhanssk/MyMavenToGradle.git'
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
                sh 'java -jar build/libs/*.jar'
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
