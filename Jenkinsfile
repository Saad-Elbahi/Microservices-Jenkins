pipeline {
    agent any

    environment {
        DOCKER_IMAGE_TAG = 'saad-elbahi/microservices-jenkins'
    }

    tools {
        // Install Docker Compose
        dockerCompose "${DOCKER_COMPOSE_VERSION}", installationName: 'default'
        // Install Maven
        maven 'maven'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Build your services using Docker Compose
                    sh "docker-compose -f docker-compose.yml build"
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deploy your services using Docker Compose
                    sh "docker-compose -f docker-compose.yml up -d"
                }
            }
        }
    }

    post {
        always {
            // Clean up (optional)
            script {
                sh "docker-compose -f docker-compose.yml down"
            }
        }
    }
}
