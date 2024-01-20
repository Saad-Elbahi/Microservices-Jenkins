pipeline {
    agent any

    tools {
        maven 'maven'
    }

    stages {
        stage('Build and Deploy Eureka Server') {
            steps {
                script {
                    dir('EurekaServer') {
                        bat 'mvn clean install'
                        bat 'docker build -t saad-elbahi/microservices-jenkins:eureka .'
                        bat 'docker run --name EurekaServer -d -p 8761:8761 saad-elbahi/microservices-jenkins:eureka'
                    }
                }
            }
        }

        stage('Build and Deploy API Gateway') {
            steps {
                script {
                    dir('APIGateway') {
                        bat 'mvn clean install'
                        bat 'docker build -t saad-elbahi/microservices-jenkins:api-gateway .'
                        bat 'docker run --name APIGateway -d -p 8080:8080 saad-elbahi/microservices-jenkins:api-gateway'
                    }
                }
            }
        }

        stage('Build and Deploy Attendance Service') {
            steps {
                script {
                    dir('AttendanceService') {
                        bat 'mvn clean install'
                        bat 'docker build -t saad-elbahi/microservices-jenkins:attendance-service .'
                        bat 'docker run --name AttendanceService -d -p 8081:8081 saad-elbahi/microservices-jenkins:attendance-service'
                    }
                }
            }
        }

        stage('Build and Deploy Registration Service') {
            steps {
                script {
                    dir('RegistrationService') {
                        bat 'mvn clean install'
                        bat 'docker build -t saad-elbahi/microservices-jenkins:registration-service .'
                        bat 'docker run --name RegistrationService -d -p 8082:8082 saad-elbahi/microservices-jenkins:registration-service'
                    }
                }
            }
        }

        stage('Build and Deploy Employee Service') {
            steps {
                script {
                    dir('EmployeeService') {
                        bat 'mvn clean install'
                        bat 'docker build -t saad-elbahi/microservices-jenkins:employee-service .'
                        bat 'docker run --name EmployeeService -d -p 8083:8083 saad-elbahi/microservices-jenkins:employee-service'
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
