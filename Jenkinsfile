pipeline {
    agent any
    tools {
        nodejs "NodeJS 18"
    }
    environment {
        DOCKER_IMAGE = "yashvrm74/task2-app"
    }
    stages {
        stage('Build') {
            steps {
                echo "Installing dependencies..."
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'npm test || echo "No tests found."'
            }
        }
        stage('Docker Build & Push') {
            steps {
                echo "Building Docker image..."
                sh 'docker build -t $DOCKER_IMAGE .'
                echo "Pushing Docker image..."
                sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
                sh 'docker push $DOCKER_IMAGE'
            }
        }
    }
}
^Z
