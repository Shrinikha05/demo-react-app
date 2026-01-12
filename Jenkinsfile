pipeline {
    agent any

    environment {
        IMAGE_NAME = "shrinikha05/react-app"
    }

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/Shrinikha05/demo-react-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t $IMAGE_NAME:latest ."
            }
        }

        stage('Push Docker Image') {
    steps {
        withDockerRegistry([credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/']) {
            sh 'docker push shrinikha05/react-app:latest'
                }
            }
        }
    }
}
