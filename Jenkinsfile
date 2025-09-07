// Jenkinsfile
pipeline {
    // The 'agent' directive tells Jenkins where to run the pipeline.
    // 'any' means it can run on any available agent.
    agent any

    // Add the 'parameters' directive to define build parameters
    parameters {
        string(name: 'BUILD_VERSION', defaultValue: '1.0.0', description: 'The version of the application to build.')
        booleanParam(name: 'RUN_SECURITY_SCAN', defaultValue: true, description: 'Whether to run the security scan stage.')
        choice(name: 'DEPLOY_ENVIRONMENT', choices: ['staging', 'production'], description: 'Select the environment to deploy to.')
    }

    // The 'stages' section contains the different stages of the pipeline.
    stages {
        stage('Checkout') {
            steps {
                echo 'Fetching source code from the repository...'
                echo "Building version: ${params.BUILD_VERSION}" // Accessing the BUILD_VERSION parameter
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
            // This stage will only run if RUN_SECURITY_SCAN parameter is true
            when {
                expression {
                    return params.RUN_SECURITY_SCAN
                }
            }
            steps {
                echo 'Scanning code for security vulnerabilities...'
            }
        }
        
        stage('Deploy to Staging') {
            // This stage will only run if DEPLOY_ENVIRONMENT is 'staging'
            when {
                expression {
                    return params.DEPLOY_ENVIRONMENT == 'staging'
                }
            }
            steps {
                echo 'Deploying application to the staging environment...'
                echo "Deploying version ${params.BUILD_VERSION} to ${params.DEPLOY_ENVIRONMENT}."
            }
        }
        
        stage('Deploy to Production') {
            // This stage will only run if DEPLOY_ENVIRONMENT is 'production'
            when {
                expression {
                    return params.DEPLOY_ENVIRONMENT == 'production'
                }
            }
            steps {
                echo 'Deploying application to the production environment...'
                echo "Deploying version ${params.BUILD_VERSION} to ${params.DEPLOY_ENVIRONMENT}."
            }
        }
        
        stage('Notify') {
            steps {
                echo 'Sending deployment success notification...'
                echo "Pipeline finished for version ${params.BUILD_VERSION}."
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
