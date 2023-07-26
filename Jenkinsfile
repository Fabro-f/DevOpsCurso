pipeline {
    agent any

    environment {
        // Definicion de variables
        def imageVersion = "1.0.${env.BUILD_NUMBER}"
        def imageName = "fabrof/desafio9"
        def imageTag = "latest"
        def portNumber= 808${env.BUILD_NUMBER}
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
                    docker.image("${imageName}:${imageVersion}").run("-p ${portNumber}:80", "--name my_container")
                }
            }
        }

        stage('Run Tests') {
            steps {
                // Run your tests here (e.g., using shell commands inside the container)
                // Example: sh 'docker exec my_container ls /path/to/config/file'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    // Subir docker a dockerhub
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        docker.image("${imageName}:${imageVersion}").push()
                        docker.image("${imageName}:${imageTag}").push()
                    }
                }
            }
        }
    }
}
