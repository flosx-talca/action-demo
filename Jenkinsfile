pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Instalar dependencias') {
            steps {
                sh '''
                    docker run --rm -v "$WORKSPACE":/app -w /app node:18 bash -c "npm install"
                '''
            }
        }

        stage('Ejecutar tests') {
            steps {
                sh '''
                    docker run --rm -v "$WORKSPACE":/app -w /app node:18 bash -c "npm test"
                '''
            }
        }
    }
}
