pipeline {
    agent any

    environment {
        DOCKER_IMAGE_TAG = "saad-elbahi/microservices-jenkins"
    }

    tools {
        maven 'maven'
    }

    stages {
        stage('Build and Deploy Eureka Server') {
            steps {
                script {
                    dir('EurekaServer') {
                        sh 'mvn clean install'
                        sh "docker build -t $DOCKER_IMAGE_TAG/eurekaserver ."
                        sh 'docker run --name EurekaServer -d -p 8761:8761 $DOCKER_IMAGE_TAG/eurekaserver'
                    }
                }
            }
        }

        stage('Build and Deploy API Gateway') {
            steps {
                script {
                    dir('APIGateway') {
                        sh 'mvn clean install'
                        sh "docker build -t $DOCKER_IMAGE_TAG/apigateway ."
                        sh 'docker run --name APIGateway -d -p 8765:8765 $DOCKER_IMAGE_TAG/apigateway'
                    }
                }
            }
        }

        stage('Build and Deploy Attendance Service') {
            steps {
                script {
                    dir('AttendanceService') {
                        sh 'mvn clean install'
                        sh "docker build -t $DOCKER_IMAGE_TAG/attendanceservice ."
                        sh 'docker run --name AttendanceService -d -p 8081:8081 $DOCKER_IMAGE_TAG/attendanceservice'
                    }
                }
            }
        }

        stage('Build and Deploy Registration Service') {
            steps {
                script {
                    dir('RegistrationService') {
                        sh 'mvn clean install'
                        sh "docker build -t $DOCKER_IMAGE_TAG/registrationservice ."
                        sh 'docker run --name RegistrationService -d -p 8082:8082 $DOCKER_IMAGE_TAG/registrationservice'
                    }
                }
            }
        }

        stage('Build and Deploy Employee Service') {
            steps {
                script {
                    dir('EmployeeService') {
                        sh 'mvn clean install'
                        sh "docker build -t $DOCKER_IMAGE_TAG/employeeservice ."
                        sh 'docker run --name EmployeeService -d -p 8083:8083 $DOCKER_IMAGE_TAG/employeeservice'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
