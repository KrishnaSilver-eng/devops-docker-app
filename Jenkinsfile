pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/KrishnaSilver-eng/devops-docker-app.git'
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
                  docker rm -f devops-docker-container || true
                  docker run -d -p 8081:80 --name devops-docker-container devops-docker-app
                '''
            }
        }
    }
}
