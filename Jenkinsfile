pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/premc5731/swift-reply.git'
            }
        }

        stage('Build Project') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        stage('Deploy Application') {
            steps {
                bat 'java -jar target/*.jar'
            }
        }
    }

    post {
        always {
            cleanWs()
            echo 'Pipeline finished.'
        }
    }
}

