pipeline {
  agent any
  stages {
    stage('Build and Run Docker Compose') {
      steps {
        sh 'pwd'
        sh 'docker-compose up -d'
      }
    }

  }
  post {
    always {
      script {
        sh 'docker-compose down'
      }

    }

  }
}
