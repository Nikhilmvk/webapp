pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Nikhilmvk/webapp.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t webapplication:latest .'
            }
        }

        stage('Run Web App') {
            steps {
                sh '''
                docker stop webapplication || true
                docker rm webapplication || true
                docker run -d --name webappss -p 8070:80 webapplication:latest
                '''
            }
        }
    }
}
