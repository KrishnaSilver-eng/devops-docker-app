pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main',
                url: 'https://github.com/KrishnaSilver-eng/devops-docker-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-docker-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f devops-docker-app || true
                docker run -d -p 8081:80 --name devops-docker-app devops-docker-app
                '''
            }
        }
    }
}
