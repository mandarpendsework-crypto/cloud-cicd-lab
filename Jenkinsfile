pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/mandarpendsework-crypto/cloud-cicd-lab.git'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t cloud-app .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker stop cloud-app || true'
                sh 'docker rm cloud-app || true'
                sh 'docker run -d -p 5000:5000 --name cloud-app cloud-app'
            }
        }
        stage('Cleanup') {
            steps {
                sh 'docker system prune -f'
            }
        }
    }
}
