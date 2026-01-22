pipeline {
    agent any

    tools {
        nodejs 'node18'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/gayas5/Trading-UI.git'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'node -v'
                sh 'npm -v'
                sh 'npm install'
            }
        }

        stage('Build UI') {
            steps {
                sh 'CI=false npm run build'
            }
        }

        stage('Run with PM2') {
            steps {
                sh 'pm2 delete Trading-UI || true'
                sh 'pm2 start npm --name Trading-UI -- start'
            }
        }
    }
}
