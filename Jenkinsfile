pipeline {
    agent any

    stages {
        stage('Listar archivos') {
            steps {
                echo '📁 Mostrando contenido del workspace raíz'
                sh 'ls -la'
                echo '📁 Mostrando contenido de la carpeta app'
                sh 'ls -la app/'
            }
        }

        stage('Instalar dependencias') {
            steps {
                echo '📦 Ejecutando npm ci en la carpeta app/'
                sh '''
                    docker run --rm \
                        -v $(pwd):/app \
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
                        -v $(pwd):/app \
                        -w /app/app \
                        node:18 \
                        bash -c "npm test"
                '''
            }
        }
    }
}
