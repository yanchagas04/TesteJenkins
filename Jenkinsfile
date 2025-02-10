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
                    sh 'add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"'
                    sh 'apt-get update'
                    sh 'apt-get install -y docker-ce docker-ce-cli containerd.io'
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
        stage('Remove Containers') {
            steps {
                script {
                    // Exibe os containers em execução
                    sh 'docker rm -f $(docker ps -aq) || true'
                }
            }
        }
        stage('Run Docker Image') {
            steps {
                script {
                    // Executa a imagem Docker na rede 'jenkins'
                    docker.image("jenkins-teste").run('--network jenkins -d -p 8000:8000')
                }
            }
        }
        stage('Show Network') {
            steps {
                script {
                    // Exibe as redes
                    sh 'docker network inspect 8345d4af37d0'
                }
            }
        }
        stage('Show Containers') {
            steps {
                script {
                    // Exibe os containers em execução
                    sh 'docker inspect jenkins-teste'
                }
            }
        }
    }
}