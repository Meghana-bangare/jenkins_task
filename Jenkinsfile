pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\pipeline task"
        TESTING_ENVIRONMENT = "nextjs-app-testing-environment"
        PRODUCTION_ENVIRONMENT = "MeghanaBangare_nextjs-app-production-environment"
        JENKINS_LOG_PATH = "C:\\ProgramData\\Jenkins\\.jenkins\\jobs\\Github-Jenkins-pipeline\\builds\\21\\log"
        EMAIL_RECIPIENT = 'meghanabangare@gmail.com'  // Your email address for notifications
    }

    stages {
        stage('Build') {
            steps {
                echo 'Build Stage'
                // Add your build tool like Maven or Gradle if necessary
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Testing Stage'
                // Run unit tests using JUnit or integration tests using Selenium
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Code Analysis Stage'
                // Integrate a code analysis tool like SonarQube or Checkstyle
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Security Stage'
                // Perform a security scan using tools like OWASP ZAP or SonarQube
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deployment Stage'
                // Deploy the application to a staging server, e.g., AWS EC2
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Integration Stage'
                // Run integration tests on the staging environment
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Production Stage'
                // Deploy the application to a production server, e.g., AWS EC2
            }
        }
    }

    post {
        always {
            echo 'Pipeline Completed.'
            emailext (
                to: "${EMAIL_RECIPIENT}",
                subject: "Pipeline Status - ${currentBuild.fullDisplayName}: ${currentBuild.currentResult}",
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
            emailext (
                to: "${EMAIL_RECIPIENT}",
                subject: "Pipeline Status - Success",
                body: "Pipeline succeeded. All stages completed successfully."
            )
        }
        failure {
            echo 'Pipeline failed!'
            emailext (
                to: "${EMAIL_RECIPIENT}",
                subject: "Pipeline Status - Failure",
                body: "Pipeline failed. Check logs for more details."
            )
        }
    }
}



