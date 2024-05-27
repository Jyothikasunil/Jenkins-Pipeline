pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                echo "Building the code using Maven"
            }
        }

        stage("Unit and Integration Tests") {
            steps {
                echo "Running unit tests with JUnit"
                echo "Running integration tests with Selenium"
            }
        }

        stage("Code Analysis") {
            steps {
                echo "Running code analysis with SonarQube"
            }
        }

        stage("Security Scan") {
            steps {
                echo "Running security scan with OWASP ZAP"
            }
        }

        stage("Deploy to Staging") {
            steps {
                echo "Deploying the application to staging server using AWS CodeDeploy"
            }
        }

        stage("Integration Tests on Staging") {
            steps {
                echo "Running integration tests on the staging environment with Selenium"
            }
        }

        stage("Deploy to Production") {
            steps {
                echo "Deploying the application to production server using AWS CodeDeploy"
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/*.log', allowEmptyArchive: true
        }
        success {
            script {
                def logFiles = findFiles(glob: '**/target/*.log')
                emailext (
                    to: 'jyothikasunil006@gmail.com',
                    subject: 'Build status email - SUCCESS',
                    body: 'Build was successful',
                    attachmentsPattern: logFiles.collect { it.path }.join(',')
                )
            }
        }
        failure {
            script {
                def logFiles = findFiles(glob: '**/target/*.log')
                emailext (
                    to: 'jyothikasunil006@gmail.com',
                    subject: 'Build status email - FAILURE',
                    body: 'Build failed',
                    attachmentsPattern: logFiles.collect { it.path }.join(',')
                )
            }
        }
    }
}
