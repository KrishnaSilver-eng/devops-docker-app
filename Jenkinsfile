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
                  docker rm -f devops-app || true
                  docker run -d --name devops-app -p 8081:80 devops-docker-app
                '''
            }
        }
    }
}
