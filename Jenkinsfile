pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nginx-static-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8080:80 --name nginx-app nginx-static-app || echo "Container might already be running."'
            }
        }
    }

    post {
        failure {
            echo 'Deployment failed.'
        }
    }
}
