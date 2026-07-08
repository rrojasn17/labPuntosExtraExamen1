pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Detener ambiente') {
            steps {
                sh 'docker compose down'
            }
        }

        stage('Levantar ambiente') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Verificar despliegue') {
            steps {
                sh 'docker ps'
            }
        }
    }
}
