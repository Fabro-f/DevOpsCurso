pipeline {
  agent {
    docker {
      image 'nginx:1.25.1-alpine'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t desafio10'
      }
    }

    stage('Run') {
      steps {
        sh 'docker run -p 8081:80 desafio10'
      }
    }

  }
}