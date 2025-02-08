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
                    sh 'docker build -t jenkins-teste:v${env.BUILD_ID} .'
                }
            }
        }
        // stage('Run Docker Image') {
        //     steps {
        //         script {
        //             // Executa a imagem Docker na rede 'jenkins'
        //             docker.image("jenkins-teste:v${env.BUILD_ID}").run('--network jenkins')
        //         }
        //     }
        // }
    }
}