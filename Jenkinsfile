pipeline {
    agent any

    stages {
        // Clone the repository (optional)
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/dheepakkh/PES1UG22CS175_Jenkins.git']]
                ])
            }
        }

        // Build stage
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'g++ PES1UG22CS175.cpp -o PES1UG22CS175'
            }
        }

        // Test stage
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh './PES1UG22CS175'
            }
        }

        // Deploy stage
        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
            error "Build or tests failed. Please check the logs."
        }
    }
}
