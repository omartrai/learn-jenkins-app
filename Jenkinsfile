pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-bullseye'  // Use Debian-based Node.js image
                    args '--user root'        // Run container as root
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "Checking file structure..."
                    ls -la
                    echo "Node.js Version:"
                    node --version
                    echo "NPM Version:"
                    npm --version
                    echo "Installing Dependencies..."
                    npm ci || (npm install --package-lock-only && npm ci)
                    echo "Verifying node_modules..."
                    ls -la node_modules || echo "node_modules missing!"
                    echo "Building Application..."
                    npm run build
                    echo "Build Completed. Listing Files:"
                    ls -la
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build completed successfully!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
