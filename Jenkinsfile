pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\pipeline task"
        EMAIL_RECIPIENT = 'meghanabangare@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Specify a build automation tool here, such as Maven or Gradle
                // sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality...'
                // Specify a code analysis tool like SonarQube or Checkstyle
                // sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Specify a security scanning tool like OWASP Dependency-Check
                // sh 'dependency-check'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server...'
                // Use tools like AWS CLI to deploy to EC2
                // sh 'aws ec2 deploy ...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // sh 'run staging tests'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                // sh 'aws ec2 deploy ...'
            }
        }
    }

    post {
        always {
            echo 'Sending email notification...'
            emailext (
                to: "${EMAIL_RECIPIENT}",
                subject: "Jenkins Pipeline - ${currentBuild.currentResult}",
                body: "The Jenkins Pipeline has finished with status: ${currentBuild.currentResult}",
                attachLog: true
            )
        }
    }
}
