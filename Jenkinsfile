pipeline {
    agent any

    stages {
        stage('Verificar estructura') {
            steps {
                echo '📂 Explorando estructura del workspace'
                sh 'find . -type f'
            }
        }

        stage('Instalar dependencias') {
            steps {
                echo '📦 Ejecutando npm ci en la raíz'
                sh '''
                    docker run --rm \
                        -v "$WORKSPACE:/app" \
                        -w /app \
                        node:18 \
                        bash -c "npm ci"
                '''
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Ejecutando pruebas'
                sh '''
                    docker run --rm \
                        -v "$WORKSPACE:/app" \
                        -w /app \
                        node:18 \
                        bash -c "npm test"
                '''
            }
        }
    }
}
