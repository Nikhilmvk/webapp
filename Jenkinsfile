pipeline {
  agent any

  stages {

    stage('Checkout') {
      steps {
        git branch: 'main',
            url: 'https://github.com/your-org/webapp.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t webapp:latest .'
      }
    }

    stage('Deploy Web App') {
      steps {
        sh '''
          docker stop webapp || true
          docker rm webapp || true

          docker run -d \
            --name webapplication \
            -p 87:80 \
            webapp:latest
        '''
      }
    }
  }
}

