// Jenkinsfile
pipeline {
    // The 'agent' directive tells Jenkins where to run the pipeline.
    // 'any' means it can run on any available agent.
    agent any

    // The 'stages' section contains the different stages of the pipeline.
    stages {
        stage('Checkout') {
            steps {
                echo 'Fetching source code from the repository...'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Starting the build process...'
                echo 'Compiling the application...'
            }
        }
        
        stage('Unit Test') {
            steps {
                echo 'Running unit tests to ensure functionality...'
            }
        }
        
        stage('Integration Test') {
            steps {
                echo 'Running integration tests to verify component interactions...'
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'Scanning code for security vulnerabilities...'
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to the staging environment...'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to the production environment...'
            }
        }
        
        stage('Notify') {
            steps {
                echo 'Sending deployment success notification...'
            }
        }
    }
    
    // The 'post' section runs after the main pipeline completes.
    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
    }
}
