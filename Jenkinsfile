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
        post {
        success {
            mail to: "sakshiranan22@gmail.com",
            subject: "Build status email",
            body: "Build was successfull"
        }
        failure {
            mail to: "sakshiranan22@gmail.com",
            subject: "Build status email",
            body: "Build was failed"
        }
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
            post {
           success {
            mail to: "jyothikasunil006@gmail.com",
            subject: "Build status email",
            body: "Build was successfull"
        }
        failure {
            mail to: "jyothikasunil006@gmail.com",
            subject: "Build status email",
            body: "Build was failed"
        }
    }
        }

        stage("Deploy to Production") {
            steps {
                echo "Deploying the application to production server using AWS CodeDeploy"
            }
        }
    }

}