pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/prabeshx12/docker-lab.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Build stage completed"'
            }
        }

        stage('Deploy using Ansible') {
            steps {
                sh 'ansible-playbook -i ansible-deploy/inventory ansible-deploy/deploy.yml'
            }
        }

        stage('Test App') {
            steps {
                sh 'curl http://localhost:5000'
            }
        }
    }
}
