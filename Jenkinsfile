pipeline {
    agent any

    stages {

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

