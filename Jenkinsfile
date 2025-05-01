pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
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
                sh 'npm run build'
            }
        }
        
        stage('Docker Build') {
            steps {
                sh 'docker build -t gericht-react-app .'
            }
        }
        
        stage('Docker Push') {
            steps {
                echo 'This is where you would push to your Docker registry'
                // sh 'docker push your-registry/gericht-react-app:latest'
            }
        }
    }
}