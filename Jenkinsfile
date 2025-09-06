pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                echo "Cloning repository..."
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh 'docker build -t my-web-app .'
            }
        }
        stage('Run Docker Container') {
            steps {
                echo "Running Docker container..."
                sh 'docker run -d -p 8080:80 --name my-web-app my-web-app || true'
            }
        }
    }
    post {
        always {
            echo "Pipeline completed."
        }
        success {
            echo "Application deployed successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
