pipeline {
    agent any

    stages {
                stage('Build and Deploy Eureka Server') {
                    steps {
                        script {
                            dir('EurekaServer') {
                                bat 'mvn clean install'
                                bat 'docker build -t ./microservices-jenkins .'
                                bat 'docker run --name eureka-server -d -p 8761:8761 ./microservices-jenkins'
                            }
                        }
                    }
                }
                stage('Build and Deploy API Gateway') {
                    steps {
                        script {
                            dir('APIGateway') {
                                bat 'mvn clean install'
                                bat 'docker build -t ./microservices-jenkins .'
                                bat 'docker run --name api-gateway -d -p 8080:8080 ./microservices-jenkins'
                            }
                        }
                    }
                }
                stage('Build and Deploy Attendance Service') {
                    steps {
                        script {
                            dir('AttendanceService') {
                                bat 'mvn clean install'
                                bat 'docker build -t ./microservices-jenkins .'
                                bat 'docker run --name attendance-service -d -p 8081:8081 ./microservices-jenkins'
                            }
                        }
                    }
                }
                stage('Build and Deploy Registration Service') {
                    steps {
                        script {
                            dir('RegistrationService') {
                                bat 'mvn clean install'
                                bat 'docker build -t ./microservices-jenkins .'
                                bat 'docker run --name registration-service -d -p 8082:8082 ./microservices-jenkins'
                            }
                        }
                    }
                }
                stage('Build and Deploy Employee Service') {
                    steps {
                        script {
                            dir('EmployeeService') {
                                bat 'mvn clean install'
                                bat 'docker build -t ./microservices-jenkins .'
                                bat 'docker run --name employee-service -d -p 8083:8083 ./microservices-jenkins'
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
