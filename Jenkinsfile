pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\pipeline task"
        EMAIL_RECIPIENT = 'meghanabangare@gmail.com'  // Your email address for notifications
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // You can specify a build tool like Maven or Gradle here
                // For now, just print the message
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
            }
        }
    }

    post {
        always {
            echo 'Sending email notification...'
            emailext (
                to: "${EMAIL_RECIPIENT}",
                subject: "Jenkins Pipeline Status - ${currentBuild.fullDisplayName}: ${currentBuild.currentResult}",
                body: """
                    Hello,

                    The Jenkins Pipeline '${currentBuild.fullDisplayName}' has finished with status: ${currentBuild.currentResult}.
                    
                    Check the logs for more details.
                    
                    Regards,
                    Jenkins CI Server
                """,
                attachLog: true
            )
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}

