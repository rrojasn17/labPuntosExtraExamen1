pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
        disableConcurrentBuilds()
    }

    stages {
        stage('Checkout desde Git') {
            steps {
                checkout scm
            }
        }

        stage('Detener contenedores') {
            steps {
                sh 'docker compose down'
            }
        }

        stage('Levantar contenedores') {
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