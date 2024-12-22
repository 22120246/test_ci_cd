pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "my_app"
        DOCKER_CONTAINER = "my_app_container"
    }

    stages {
        stage('Say hello') {
            steps {
                // Clone repository từ GitHub
                echo "Hello-world"
            }
        }

    }

    post {
        always {
            // Hiển thị danh sách container và logs để kiểm tra
            sh 'sudo docker ps -a'
        }
        success {
            echo 'Done updated!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
