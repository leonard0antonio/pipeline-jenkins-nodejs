pipeline {
    agent any

    tools {
        nodejs 'NodeJS' 
    }

    stages {
        stage('Instalar dependências') {
            steps {
                echo 'Instalando os pacotes do Node.js...'
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Executando o build do projeto...'
                bat 'npm run build --if-present'
            }
        }

        stage('Teste') {
            steps {
                echo 'Rodando a suíte de testes...'
                bat 'npm test'
            }
        }
    }

    post {
        success {
            echo '✅ SUCESSO: O pipeline foi concluído sem erros.'
        }
        failure {
            echo '❌ FALHA: O pipeline encontrou um erro.'
        }
        always {
            echo 'Limpando o workspace...'
            cleanWs()
        }
    }
}