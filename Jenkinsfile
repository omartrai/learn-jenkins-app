pipeline {
  agent {
    docker {
      image 'node:18-alpine'
      args '-u root' // Run as root to avoid permission issues
    }
  }
  stages {
    stage('Clean Workspace') {
      steps {
        sh 'rm -rf node_modules package-lock.json'
      }
    }
    stage('Install Dependencies') {
      steps {
        sh 'npm ci'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
  }
}