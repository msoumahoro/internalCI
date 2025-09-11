// Jenkinsfile-Test webhook
pipeline {
    agent any

    parameters {
        string(name: 'BUILD_VERSION', defaultValue: '1.0.0', description: 'App version')
        booleanParam(name: 'RUN_SECURITY_SCAN', defaultValue: true, description: 'Run the security scan')
        choice(name: 'DEPLOY_TARGET', choices: ['staging', 'production', 'both'], description: 'Where to deploy')
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Fetching source code..."
                echo "Building version: ${params.BUILD_VERSION}"
            }
        }

        stage('Build') {
            steps {
                echo 'Build...'
                echo 'Compile...'
            }
        }

        stage('Unit Test') {
            steps {
                echo 'Run unit tests...'
            }
        }

        stage('Integration Test') {
            steps {
                echo 'Run integration tests...'
            }
        }

        stage('Security Scan') {
            when { expression { params.RUN_SECURITY_SCAN } }
            steps {
                echo 'Security scan...'
            }
        }

        stage('Deploy to Staging') {
            when { expression { params.DEPLOY_TARGET in ['staging', 'both'] } }
            steps {
                echo "Deploying ${params.BUILD_VERSION} to staging"
                // sh './deploy.sh staging'
            }
        }

        stage('Post Staging Checks') {
            when { expression { params.DEPLOY_TARGET == 'both' } }
            steps {
                echo 'Smoke checks after staging...'
                // put automated checks here if you want gates without humans
            }
        }

        stage('Deploy to Production') {
            when { expression { params.DEPLOY_TARGET in ['production', 'both'] } }
            steps {
                echo "Deploying ${params.BUILD_VERSION} to production"
                // sh './deploy.sh production'
            }
        }

        stage('Notify') {
            steps {
                echo "Pipeline finished for version ${params.BUILD_VERSION}"
            }
        }
    }

    post {
        always { echo 'Pipeline finished.' }
        success { echo 'Pipeline completed successfully.' }
        failure { echo 'Pipeline failed. Check logs for details.' }
    }
}
