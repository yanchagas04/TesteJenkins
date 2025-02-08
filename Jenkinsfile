pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    // Clona a branch 'main' do repositório
                    git url: 'https://github.com/yanchagas04/TesteJenkins.git', branch: 'main'
                }
            }
        }
        stage('Create Network') {
            steps {
                script {
                    // Cria a rede 'jenkins'
                    sh 'docker network create jenkins || true'
                }
            }
        }
        stage('Check Docker Version') {
            steps {
                script {
                    // Verifica a versão do Docker
                    sh 'docker --version'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Constrói a imagem Docker
                    docker.build("jenkins-teste", '.')
                }
            }
        }
        stage('Run Docker Image') {
            steps {
                script {
                    // Executa a imagem Docker na rede 'jenkins'
                    docker.image("jenkins-teste").run('--network jenkins')
                }
            }
        }
        stage('Show Containers') {
            steps {
                script {
                    // Exibe os containers em execução
                    sh 'docker ps'
                }
            }
        }
        stage('Show IP') {
            steps {
                script {
                    // Exibe as redes
                    sh 'docker inspect jenkins-teste'
                }
            }
        }
    }
}