pipeline {
    agent any

    environment {
        APP_NAME = 'my-website'
        DEPLOY_DIR = '/var/www/html'
    }

    stages {

        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'sudo cp -r * ${DEPLOY_DIR}/'
                sh 'echo "Site is LIVE at http://13.233.90.57"'
            }
        }
    }

    post {
        success { echo 'Deployment SUCCESSFUL!' }
        failure  { echo 'Build FAILED — Check logs' }
    }
}
