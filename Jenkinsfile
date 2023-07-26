pipeline {
  agent any
  stages {
    stage('Build Docker Image') {
      steps {
        sh '''def dockerfile = \'./path/to/your/Dockerfile\'
docker.build("${imageName}:${imageVersion}", "-t ${imageName}:${imageTag} -f ${dockerfile} .")'''
      }
    }

    stage('Run Container') {
      steps {
        sh 'docker.image("${imageName}:${imageVersion}").run("-p 8082:80", "--name my_container")'
      }
    }

  }
  environment {
    imageVersion = '1.0.${env.BUILD_NUMBER}'
    imageName = 'fabrof/desafio9'
    imageTag = 'latest'
  }
}