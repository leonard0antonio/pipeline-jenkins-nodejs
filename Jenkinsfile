pipeline {
    agent any

    tools {
            
        nodejs 'NodeJS' 
    }

    stages {
        stage('Instalar dependências') {
            steps {
                echo 'Instalando os pacotes do Node.js...'
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Executando o build do projeto...'
                sh 'npm run build --if-present'
            }
        }

        stage('Teste') {
            steps {
                echo 'Rodando a suíte de testes...'
                sh 'npm test'
            }
        }
    }

    post {
        success {
            echo '✅ SUCESSO: O pipeline foi concluído sem erros. O build e os testes passaram!'
        }
        failure {
            echo '❌ FALHA: O pipeline encontrou um erro em uma das etapas. Verifique os logs.'
        }
        always {
            echo 'Limpando o workspace após a execução...'
            cleanWs()
        }
    }
}