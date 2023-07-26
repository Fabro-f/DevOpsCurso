pipeline {
    agent any

    environment {
        // Define variables for image versioning
        def imageVersion = "1.0.${env.BUILD_NUMBER}"
        def imageName = "fabrof/desafio9"
        def imageTag = "latest"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Set the Dockerfile path
                    def dockerfile = './path/to/your/Dockerfile'
                    
                    // Build the Docker image and tag it with version number
                    docker.build("${imageName}:${imageVersion}", "-t ${imageName}:${imageTag} -f ${dockerfile} .")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // Run the Docker container using the built image
                    docker.image("${imageName}:${imageVersion}").run("-p 8082:80", "--name my_container")
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
                    // Push the built image to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        docker.image("${imageName}:${imageVersion}").push()
                        docker.image("${imageName}:${imageTag}").push()
                    }
                }
            }
        }
    }
}
