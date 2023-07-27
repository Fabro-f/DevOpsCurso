pipeline {
    agent any

    environment {
        // Definicion de variables
        def dockerhub_credentials = 'dockerhub_credential'
        def imageVersion = "1.0.${env.BUILD_NUMBER}"
        def imageName = "fabrof/desafio9"
        def imageTag = "latest"
        def portNumber= "80${env.BUILD_NUMBER}"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Definicion del path 
                    def dockerfile = '/home/vagrant/Dockerfile'
                    
                    // Build Docker imagen
                    docker.build("${imageName}:${imageVersion}", "-t ${imageName}:${imageTag} -f ${dockerfile} .")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // Run Docker container
                    docker.image("${imageName}:${imageVersion}").run( "-p ${portNumber}:80 --name desafio10", "")
                }
            }
        }

    stage('Tests') {
         steps {
                sh 'docker exec desafio10 ls /usr/share/nginx/html'
            }
        }

        stage('Push to Docker Hub') {
            steps {
               script {
                   //Subir docker a dockerhub
                   docker.withRegistry('', dockerhub_credentials) 
                   {
                   docker.image("${imageName}:${imageVersion}").push()
                   docker.image("${imageName}:${imageTag}").push()
                   }
                }
           }
        }
    }
}
