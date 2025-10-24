pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t registration:v1 .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                bat 'docker tag registration:v1 nabeela04/registration:v1'
                bat 'docker push nabeela04/registration:v1'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }

        stage('AutomTated UI Test') {
            steps {
                echo 'Starting UI test...'
                bat 'python D:/DevOps/week-2/test_registration.py'
            }
        }
    }
}
