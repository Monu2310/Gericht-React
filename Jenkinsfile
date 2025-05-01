pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS' // This assumes you have NodeJS configured in Jenkins Global Tool Configuration
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm -v'
                sh 'node -v'
                sh 'npm install'
            }
        }
        
        stage('Run Tests') {
            steps {
                sh 'npm test -- --passWithNoTests'
            }
        }
        
        stage('Build') {
            steps {
                // Set CI=false to prevent ESLint warnings from being treated as errors
                sh 'CI=false npm run build'
            }
        }
        
        stage('Check Docker Installation') {
            steps {
                script {
                    try {
                        sh 'which docker || echo "Docker not found"'
                        sh 'docker --version || echo "Docker not available"'
                    } catch(Exception e) {
                        echo "Docker is not installed or not in PATH. Skipping Docker stages."
                        echo "To enable Docker builds, make sure Docker is installed and available to the Jenkins user."
                    }
                }
            }
        }
        
        stage('Docker Build') {
            when {
                expression {
                    try {
                        sh(script: 'which docker', returnStatus: true) == 0
                    } catch(Exception e) {
                        return false
                    }
                }
            }
            steps {
                sh 'docker build -t gericht-react-app .'
            }
        }
        
        stage('Docker Push') {
            when {
                expression {
                    try {
                        sh(script: 'which docker', returnStatus: true) == 0
                    } catch(Exception e) {
                        return false
                    }
                }
            }
            steps {
                echo 'This is where you would push to your Docker registry'
                // sh 'docker push your-registry/gericht-react-app:latest'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline completed successfully! React application built successfully.'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
        always {
            echo 'Cleaning up workspace...'
            // Add cleanup steps if needed
        }
    }
}