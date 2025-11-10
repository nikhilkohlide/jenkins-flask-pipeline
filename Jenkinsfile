pipeline {
     agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials')
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    def app = docker.build("myapp:latest")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', "$DOCKERHUB_CREDENTIALS") {
                        def app = docker.image("myapp:latest")
                        app.push()
                    }
                }
            }
        }
    }
}

