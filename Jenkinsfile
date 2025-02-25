pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18'
                    reuseNode true
                    args '--memory=2g --cpus=2'
                }
            }
            steps {
                sh '''
                    echo "Checking Environment..."
                    ls -la
                    node --version
                    npm --version
                    cat package.json

                    echo "Cleaning Cache..."
                    npm cache clean --force

                    echo "Installing Dependencies..."
                    npm install

                    echo "Checking Installed Packages..."
                    ls -la node_modules/.bin
                    npx react-scripts --version || echo "react-scripts not found!"

                    echo "Building the Project..."
                    npm run build

                    echo "Build Complete!"
                    ls -la
                '''
            }
        }
    }
}
