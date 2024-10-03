pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\pipeline task"
        TESTING_ENVIRONMENT = "nextjs-app-testing-environment"
        PRODUCTION_ENVIRONMENT = "MeghanaBangare_nextjs-app-production-environment"
        JENKINS_LOG_PATH = "C:\\ProgramData\\Jenkins\\.jenkins\\jobs\\Github-Jenkins-pipeline\\builds\\21\\log"
        EMAIL_RECIPIENT = "meghanabangare@gmail.com"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Build Stage'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Testing Stage'
            }
            post {
                success {
                    emailext (
                        to: "${EMAIL_RECIPIENT}",
                        subject: "Unit and Integration Tests - Success",
                        body: "The Unit and Integration Tests have passed successfully.",
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: "${EMAIL_RECIPIENT}",
                        subject: "Unit and Integration Tests - Failure",
                        body: "The Unit and Integration Tests failed. Check logs for more details.",
                        attachLog: true
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Code Analysis Stage'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Security Stage'
            }
            post {
                success {
                    emailext (
                        to: "${EMAIL_RECIPIENT}",
                        subject: "Security Scan - Success",
                        body: "The Security Scan completed successfully.",
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: "${EMAIL_RECIPIENT}",
                        subject: "Security Scan - Failure",
                        body: "The Security Scan failed. Check logs for more details.",
                        attachLog: true
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deployment Stage'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Integration Stage'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Production Stage'
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
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
