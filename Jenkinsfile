pipeline {
    agent {
        docker {
            image 'node:18-alpine'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'node --version'
                sh 'npm --version'
                
                // First run npm install instead of npm ci
                sh 'npm install'
                
                // Then build the application
                sh 'npm run build'
            }
        }
    }
}