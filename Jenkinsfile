pipeline {
    agent any

    environment {
        DOCKER_IMAGE_NAME = 'hello-world-python:latest' // Docker image name
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/PJAlgoMaster/jenkins_docker_python_hello_world.git'
            }
        }

        stage('Docker Build') {
            steps {
                script {
                    if (fileExists('Dockerfile')) {
                        sh "docker build -t ${DOCKER_IMAGE_NAME} ."
                    } else {
                        error 'Dockerfile not found in the workspace'
                    }
                }
            }
        }

        stage('Docker Run (optional)') {
            steps {
                sh "docker run --rm ${DOCKER_IMAGE_NAME}"
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs for details.'
        }
    }
}
