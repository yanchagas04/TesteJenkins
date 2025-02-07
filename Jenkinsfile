pipeline {
    agent any
    
    environment {
        DOCKER_TLS_VERIFY = '0' // Desabilita a verificação TLS
        DOCKER_HOST = 'tcp://your-docker-host:2376' // Altere para o seu host Docker
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    // Clona a branch 'main' do repositório
                    git url: 'https://github.com/yanchagas04/TesteJenkins.git', branch: 'main'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Constrói a imagem Docker
                    echo "Construindo a imagem Docker..."
                }
            }
        }
        stage('Run Docker Image') {
            steps {
                script {
                    // Executa a imagem Docker na rede 'jenkins'
                    echo "Executando a imagem Docker na rede 'jenkins'..."
                }
            }
        }
    }
}