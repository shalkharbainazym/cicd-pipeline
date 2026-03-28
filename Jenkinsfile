pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Кодты GitHub-тан алу
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                // Docker имиджін жинау (main нұсқасы)
                sh 'docker build -t my-app-main .'
            }
        }

        stage('Test') {
            steps {
                // Тесттерді симуляциялау (немесе нақты тесттерді іске қосу)
                echo 'Running unit tests on Main branch...'
            }
        }

        stage('Deploy to Production') {
            steps {
                // Ескі контейнерді өшіріп, жаңасын 8081 портында іске қосу
                // (dev 3000-да болса, main-ді 8081-ге қойған ыңғайлы)
                sh 'docker rm -f react-main-container || true'
                sh 'docker run -d -p 8081:3000 --name react-main-container my-app-main'
                echo 'Application deployed to http://localhost:8081'
            }
        }
    }
}
