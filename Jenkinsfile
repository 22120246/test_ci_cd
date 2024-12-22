pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "my_app"
        DOCKER_CONTAINER = "my_app_container"
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clone repository từ GitHub
                git branch: 'main', url: 'https://github.com/22120246/test_ci_cd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Xây dựng Docker image từ Dockerfile
                sh 'sudo docker build -t ${DOCKER_IMAGE} .'
            }
        }

        stage('Run Docker Container') {
            steps {
                // Dừng container cũ (nếu có)
                script {
                    sh 'sudo docker stop ${DOCKER_CONTAINER} || true'
                    sh 'sudo docker rm ${DOCKER_CONTAINER} || true'
                }
                // Chạy container mới
                sh 'sudo docker run -d --name ${DOCKER_CONTAINER} -p 5000:5000 ${DOCKER_IMAGE}'
            }
        }
    }

    post {
        always {
            // Hiển thị danh sách container và logs để kiểm tra
            sh 'docker ps -a'
        }
        success {
            echo 'Done updated!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
