pipeline {
    agent any
     tools {
            maven 'maven'
        }
    stages {
        stage('Deploy') {
            steps {
                script {
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
