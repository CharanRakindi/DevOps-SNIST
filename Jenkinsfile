pipeline {
    agent any

    environment {
        APP_NAME = 'my-website'
        DEPLOY_DIR = '/var/www/html'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/CharanRakindi/DevOps-SNIST.git'
            }
        }

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

        stage('Terraform') {
            steps {
                dir('terraform') {
                    sh 'terraform init'
                    sh 'terraform apply -auto-approve'
                }
            }
        }

        stage('Deploy') {
            steps {
                sh 'sudo cp -r * ${DEPLOY_DIR}/'
                sh 'echo "Deployment SUCCESSFUL!"'
            }
        }
    }

    post {
        success { echo 'Deployment SUCCESSFUL!' }
        failure { echo 'Build FAILED — Check logs' }
    }
}
