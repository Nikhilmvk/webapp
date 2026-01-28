pipeline {
  agent any

  stages {

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t webapplication:latest .'
      }
    }

    stage('Deploy Web App') {
      steps {
        sh '''
          docker stop webapp || true
          docker rm webapp || true
          docker run -d --name webapp -p 87:80 webapp:latest
        '''
      }
    }
  }
}
