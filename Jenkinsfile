pipeline {
  agent {
    docker {
      image 'nginx:1.25.1-alpine'
      args '-p 8081:80'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

  }
}