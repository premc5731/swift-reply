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
                script {
                    def files = findFiles(glob: 'target/*.jar')
                    
                    if (files.size() > 0) {
                        def jarPath = files[0].path
                        echo "Attempting to run ${jarPath}"
                        
                        bat "java -jar ${jarPath}"
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

