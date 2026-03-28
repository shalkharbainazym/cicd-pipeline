pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                checkout scm
            }
        }
        stage('Docker Build') {
            steps {
                // Имиджді жинау
                sh 'docker build -t my-react-app .'
            }
        }
        stage('Docker Run') {
            steps {
                // Егер ескі контейнер болса, оны тоқтатып, өшіру
                sh 'docker stop react-container || true'
                sh 'docker rm react-container || true'
                // Жаңасын 3000 портында іске қосу
                sh 'docker run -d -p 3000:3000 --name react-container my-react-app'
            }
        }
    }
}
