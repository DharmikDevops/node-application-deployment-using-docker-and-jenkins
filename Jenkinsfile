pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'dharmikmala/my-node-docker-app'
        DOCKER_TAG = 'latest'
    }

    stages {
        stage('Checkout') {
            steps {
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
                script {
                    docker.build("${DOCKER_IMAGE}:${DOCKER_TAG}")
                }
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh 'npm test'
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

        stage('Run Docker Container') {
            steps {
                script { 
                    sh 'docker stop my-node-container || true' // Stop existing container if running
                    sh 'docker rm my-node-container || true'   // Remove existing container if exists
                    sh 'docker run -d --name my-node-container -p 3000:3000 ${DOCKER_IMAGE}:${DOCKER_TAG}'
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
