pipeline {
    agent any

    stages {
        stage('Verificar estructura') {
            steps {
                echo '📂 Explorando estructura completa del workspace'
                sh 'find . -type f'
            }
        }

        stage('Instalar dependencias') {
            steps {
                echo '📦 Ejecutando npm ci en la carpeta app/'
                sh '''
                    docker run --rm \
                        -v "$WORKSPACE:/app" \
                        -w /app/app \
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
                        -w /app/app \
                        node:18 \
                        bash -c "npm test"
                '''
            }
        }
    }
}
