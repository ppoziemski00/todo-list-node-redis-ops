pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'todo-list-node-redis'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/ppoziemski00/todo-list-node-redis.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(env.DOCKER_IMAGE)
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    docker.image("${env.DOCKER_IMAGE}:latest").run("-p 3000:3000")
                }
            }
        }
    }
}
