pipeline {
  agent {
    docker {
      image 'node:20-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        echo 'Building'
        sh 'npm install'
      }
    }

    stage('Run') {
      steps {
        echo 'Runing'
      }
    }

    stage('test') {
      steps {
        echo 'testing'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Subiendo a dockerHub'
      }
    }

  }
}