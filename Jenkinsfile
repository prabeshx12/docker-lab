pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/prabeshx12/docker-lab.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t backend-app ./backend'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop backend || true'
                sh 'docker rm backend || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name backend backend-app'
            }
        }

        stage('Test App') {
            steps {
                sh 'curl http://localhost:5000'
            }
        }
    }
}
