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
                    // Workaround for the missing 'findFiles' step.
                    // We use a batch command to find the .jar file and write its path to a temporary file.
                    bat 'dir /b /s target\\*.jar > jarfile.tmp'
                    
                    // Read the file path from the temporary file. The .trim() removes any extra whitespace.
                    def jarPath = readFile('jarfile.tmp').trim()

                    if (jarPath && !jarPath.isEmpty()) {
                        echo "Attempting to run ${jarPath}"
                        
                        // Execute the command with the exact file path.
                        // Reminder: This step will hang if your Spring Boot server is a long-running process.
                        bat "java -jar \"${jarPath}\""
                    } else {
                        // Fail the build if no JAR file was found.
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

