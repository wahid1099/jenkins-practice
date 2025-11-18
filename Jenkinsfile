pipeline {
    agent any

    environment {
        IMAGE_NAME = "myapp"           // set your image name
        IMAGE_TAG  = "latest"          // or use: "${env.BUILD_NUMBER}"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // Stop and remove existing container if already running
                    sh "docker rm -f demo-container || true"

                    sh "docker run -d -p 5000:5000 --name demo-container ${IMAGE_NAME}:${IMAGE_TAG}"
                }
            }
        }
    }
}
