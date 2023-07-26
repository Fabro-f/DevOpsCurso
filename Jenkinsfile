pipeline {
  agent {
    docker {
      image 'nginx:1.25.1-alpine'
      args '-p 8081:8081'
    }

  }
  stages {
    stage('Build') {
      steps {
        echo 'Hello'
      }
    }

    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }

  }
  environment {
    tag = '1.0'
  }
}