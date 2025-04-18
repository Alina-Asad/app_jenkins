pipeline {
    agent any
    
    environment {
        IMAGE_NAME = 'your-image-name'
        DOCKER_REGISTRY = 'your-docker-registry' // Optional, if you're using a private registry
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from the repository
                git 'https://github.com/Alina-Asad/app_jenkins'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    docker.build("${DOCKER_REGISTRY}/${IMAGE_NAME}")
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // You can add any test scripts here, like running unit tests in your container
                    // Example: docker.image("${DOCKER_REGISTRY}/${IMAGE_NAME}").inside {
                    //     sh 'npm test'
                    // }
                }
            }
        }

        stage('Push to Docker Registry') {
            steps {
                script {
                    // Push the Docker image to the Docker registry (only if you need to)
                    docker.withRegistry('', 'docker-credentials-id') {
                        docker.image("${DOCKER_REGISTRY}/${IMAGE_NAME}").push()
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deployment steps can be added here, such as deploying the image to a server or Kubernetes
                    // Example:
