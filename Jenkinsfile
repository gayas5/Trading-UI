pipeline {
    agent any

    tools {
        nodejs 'node20'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/betawins/Trading-UI.git'
            }
        }

        stage('Verify Tools') {
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build UI') {
            steps {
                sh 'CI=false npm run build'
            }
        }

        stage('Run App with PM2') {
            steps {
                sh '''
                    npm install -g pm2
                    pm2 delete Trading-UI || true
                    pm2 start npm --name Trading-UI -- start
                '''
            }
        }
    }
}
