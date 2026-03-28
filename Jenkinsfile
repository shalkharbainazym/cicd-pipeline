pipeline {
    agent any
    environment {
        PORT = "3001"
        IMAGE_NAME = "nodedev:v1.0"
        CONTAINER_NAME = "nodedev-container"
    }
    stages {
        stage('Clone') {
            steps {
                checkout scm
            }
        }
        stage('Docker Build') {
            steps {
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }
        stage('Docker Run') {
            steps {
                sh "docker stop ${CONTAINER_NAME} || true"
                sh "docker rm ${CONTAINER_NAME} || true"
                sh "docker run -d -p ${PORT}:3000 --name ${CONTAINER_NAME} ${IMAGE_NAME}"
                echo "Dev version deployed at http://localhost:${PORT}"
            }
        }
    }
}
