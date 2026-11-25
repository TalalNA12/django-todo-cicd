pipeline {
    agent any

    options {
        disableConcurrentBuilds()
    }

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t todo .'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker rm -f django-todo 2>NUL || exit /b 0'
                bat 'docker run -d --name django-todo -p 127.0.0.1:8000:8000 todo'
            }
        }
    }
}
