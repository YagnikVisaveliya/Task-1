pipeline {
    
    agent any

    environment {
        IMAGE_NAME = 'Task-2'
        CONTAINER_NAME = 'Task-2-container'
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main', url: ''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME}:latest -t ${IMAGE_NAME}:v${BUILD_NUMBER} ."
            }
        }

        stage('Deploy on EC2') {
            steps {
                sh """
                  docker stop ${CONTAINER_NAME} || true
                  docker rm ${CONTAINER_NAME} || true
                  docker run -d --name ${CONTAINER_NAME} -p 3000:3000 ${IMAGE_NAME}:latest
                """
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }

        failure {
            echo 'Pipeline failed.'
        }

        always {
            echo 'Task-2 pipeline execution finished.'
        }
    }
}