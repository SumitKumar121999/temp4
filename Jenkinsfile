pipeline {
    agent any

    environment {
        DOCKER_IMAGE_TAG = "springboot-deploy${env.BUILD_NUMBER}"
    }

    stages {
        stage('Build and Deploy') {
            steps {
                script {
                    // Get code from a GitHub repository
                    git branch: 'main', url: 'https://github.com/SumitKumar121999/temp4.git'

                    // Build Docker image
                    def dockerImage = docker.build("springboot-deploy:${DOCKER_IMAGE_TAG}")

                    // Stop and remove existing container, if any
                    sh "docker stop springboot-deploy || true && docker rm springboot-deploy || true"

                    // Run Docker container
                    sh "docker run --name springboot-deploy -d -p 8581:8081 springboot-deploy:${DOCKER_IMAGE_TAG}"
                }
            }
        }
    }
}
