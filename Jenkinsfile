pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    docker.build("employee-service", "saad-elbahi/EmployeeService")
                    docker.build("eureka-server", "saad-elbahi/EurekaServer")
                    docker.build("attendance-service", "saad-elbahi/AttendanceService")
                    docker.build("registration-service", "saad-elbahi/RegistrationService")
                    docker.build("api-gateway", "saad-elbahi/APIGateway")
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
