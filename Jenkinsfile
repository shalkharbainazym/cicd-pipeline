pipeline {
    agent any
    environment {
        PORT = "3000"
        IMAGE_NAME = "nodemain:v1.0"
        CONTAINER_NAME = "nodemain-container"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }
        stage('Deploy') {
            steps {
                sh "docker stop ${CONTAINER_NAME} || true"
                sh "docker rm ${CONTAINER_NAME} || true"
                sh "docker run -d -p ${PORT}:3000 --name ${CONTAINER_NAME} ${IMAGE_NAME}"
                echo "Application deployed at http://localhost:${PORT}"
            }
        }
    }
}
