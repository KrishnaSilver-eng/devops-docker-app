pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-docker-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f devops-docker-app || true
                docker run -d -p 8081:80 --name devops-docker-app devops-docker-app
                '''
            }
        }
    }
}
