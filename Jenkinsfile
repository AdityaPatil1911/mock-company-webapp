pipeline {
    agent any
    tools {
        git 'Default' // Ensure Git is configured
    }
    environment {
        // Set environment variables if required
        BUILD_TOOL = 'gradle' // Example tool
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }
        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh './build.sh' // Replace with your Linux build command/script
                    } else {
                        bat 'build.bat' // Replace with your Windows build command/script
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    if (isUnix()) {
                        sh './run-tests.sh' // Replace with your Linux test command/script
                    } else {
                        bat 'run-tests.bat' // Replace with your Windows test command/script
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    if (isUnix()) {
                        sh './deploy.sh' // Replace with your Linux deploy command/script
                    } else {
                        bat 'deploy.bat' // Replace with your Windows deploy command/script
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Build and tests were successful!'
        }
        failure {
            echo 'There were failures. Please check the logs.'
        }
    }
}
