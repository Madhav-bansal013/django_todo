pipeline {
    agent any

    stages {
        stage('Stop Containers') {
            steps {
                // Stop and remove containers, networks, and volumes
                sh 'sudo docker-compose down'
            }
        }

        stage('Start Containers') {
            steps {
                // Rebuild and restart containers with no dependencies
                sh 'sudo docker-compose up -d --force-recreate --no-deps --build web'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
