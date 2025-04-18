pipeline {
    agent any

    environment {
        IMAGE_NAME = 'my-node-app'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Alina-Asad/app_jenkins'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Optional: Add test commands here if needed
                    // e.g., docker.image("${IMAGE_NAME}").inside {
                    //     sh 'npm test'
                    // }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo "Running container from image ${IMAGE_NAME}..."
                    docker.image("${IMAGE_NAME}").run("-p 3000:3000")
                }
            }
        }
    }
}
