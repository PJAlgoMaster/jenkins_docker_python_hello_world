// Jekinsfile
pipeline {
    agent any

    environment {
        DOCKER_IMAGE_NAME = 'hello-world-python:latest' // Docker image name
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url:
                'https://github.com/abhishekbadole12/practice-2.git'
            }
        }
        stage('Docker Build') {
            steps {
                scipt {
                        if (fileExists('Dockerfile')) {
                            sh "docker build -t ${env.DOCKER_IMAGE} ."
                        } else {
                            error 'Dockerfile not found in the workspace'
                        }
                }
            }
        }

        stage('Docker Run (optional)') {
            steps {
                sh "docker run --rm ${env.DOCKER_IMAGE}"
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
