pipeline {
    agent any

    environment {
        IMAGE_NAME = 'jenkins-flask-app'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                    docker stop flask || true
                    docker rm flask || true
                    docker run -d -p 5000:5000 --name flask $IMAGE_NAME
                '''
            }
        }
    }
}
