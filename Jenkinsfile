pipeline {
    agent any

    environment {
            PORT = '8081'

            API_KEY = credentials('swift-reply-api-key')
        }

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
                script {
                    bat 'dir /b /s target\\*.jar > jarfile.tmp'
                    
                    def jarPath = readFile('jarfile.tmp').trim()

                    if (jarPath && !jarPath.isEmpty()) {
                        echo "Attempting to run ${jarPath}"
                        
                        bat "java -jar \"${jarPath}\""
                    } else {
                        error "No .jar file found in target directory to deploy."
                    }
                }
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

