pipeline {
    agent any
    environment {
        GIT_REPO = 'https://github.com/mahirrehman10/trvytask.git'
        GIT_BRANCH = 'main'
        DOCKER_REGISTRY = 'localhost:5000'
        IMAGE_NAME = 'myimage'
        IMAGE_TAG = 'latest'
        DOCKERFILE_PATH = 'dockerfile'
    }
    stages {
        stage('Checkout the Git repository') {
            steps {
                git branch: "${GIT_BRANCH}", url: "${GIT_REPO}"
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    def dockerImage = docker.build("${DOCKER_REGISTRY}/${IMAGE_NAME}:${IMAGE_TAG}", "-f ${DOCKERFILE_PATH} .")
                    dockerImage.push()
                }
            }
        }
    }
}
