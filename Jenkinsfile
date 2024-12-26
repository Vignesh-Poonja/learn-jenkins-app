pipeline {
    agent any
    tools {
        git 'Default'  // Use the configured Git installation
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Vignesh-Poonja/learn-jenkins-app.git', branch: 'main'
            }
        }
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
