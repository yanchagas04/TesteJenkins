pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    git url: 'https://github.com/yanchagas04/TesteJenkins.git', branch: 'main'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerapp = docker.build("jenkins-teste:v${env.BUILD_ID}", "-f .")
                }
            }
        }
        stage('Run Docker Image') {
            steps {
                script {
                    docker.image("jenkins-teste:v${env.BUILD_ID}").run()
                }
            }
        }
    }
}