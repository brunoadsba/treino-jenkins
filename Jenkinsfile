pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'meu_projeto_flask'
    }

    stages {
        stage('Checkout') {
            steps {
                // Puxa o código do repositório
                git 'https://github.com/brunoadsba/treino-jenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Constrói a imagem Docker
                    docker.build(DOCKER_IMAGE)
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Executa testes unitários
                    docker.image(DOCKER_IMAGE).inside {
                        sh 'pytest'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Comandos para deploy da aplicação
                    echo 'Deploying application...'
                    // Adicione comandos específicos para o seu ambiente de deploy
                }
            }
        }
    }

    post {
        always {
            // Notificações ou limpeza após a execução do pipeline
            echo 'Pipeline finished.'
        }
    }
}
