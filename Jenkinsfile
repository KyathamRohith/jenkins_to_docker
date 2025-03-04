pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'rohith1305/myapp1:latest'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url:'https://github.com/KyathamRohith/jenkins_to_docker.git',branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withDockerRegistry([credentialsId: '93c470a0-e8fe-425c-8f55-932aae8919d4', url: 'https://index.docker.io/v1/']) {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
    }
}
