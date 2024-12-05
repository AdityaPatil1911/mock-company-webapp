pipeline {
    agent any

    tools {
        // Specify the JDK version you need
        jdk 'Java 11' // Replace with your JDK version name configured in Jenkins
    }

    environment {
        // Add any environment variables if required
        GRADLE_USER_HOME = '.gradle'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                bat './gradlew.bat clean build'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat './gradlew.bat test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add deployment steps here (e.g., copy files, run scripts, etc.)
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }

        always {
            echo 'Cleaning up...'
            cleanWs() // Optional: Cleans up the workspace
        }
    }
}
