pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'dharmikmala/my-node-docker-app'
        DOCKER_TAG = 'latest'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git 'https://github.com/DharmikDevops/node-docker-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build the Docker image
                script {
                    docker.build("${DOCKER_IMAGE}:${DOCKER_TAG}")
                }
            }
        }

        stage('Run Tests') {
            steps {
                // Add your testing commands here
                echo 'Running tests...'
                // Example: sh 'npm test' (if you have tests)
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        docker.build("${DOCKER_IMAGE}:${DOCKER_TAG}").push("${DOCKER_TAG}")
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up after the build'
            cleanWs()
        }
    }
}
