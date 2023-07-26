pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building'
        git(url: 'https://github.com/Fabro-f/DevOpsCurso/dockerfile', branch: 'main', credentialsId: 'Fabro-f')
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