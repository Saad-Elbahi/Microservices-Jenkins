pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                dir('EmployeeService') {
                    sh 'docker build -t employee-service .'
                }
                dir('EurekaServer') {
                    sh 'docker build -t eureka-server .'
                }
                dir('AttendanceService') {
                    sh 'docker build -t attendance-service .'
                }
                dir('RegistrationService') {
                    sh 'docker build -t registration-service .'
                }
                dir('APIGateway') {
                    sh 'docker build -t api-gateway .'
                }
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}