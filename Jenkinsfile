pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verificar estructura real') {
            steps {
                sh '''
                    echo "📂 Contenido del WORKSPACE:"
                    ls -la
                '''
            }
        }

        stage('Preparar carpeta app') {
            steps {
                sh '''
                    echo "📦 Creando carpeta app/"
                    mkdir -p app

                    echo "📄 Copiando archivos..."
                    cp -v package.json package-lock.json app/ || true
                    cp -vr src tests app/

                    echo "📂 Contenido dentro de app/:"
                    ls -la app
                '''
            }
        }

        stage('Test en Node 18') {
            steps {
                sh '''
                    echo "🚀 Ejecutando tests en contenedor Node 18"
                    docker run --rm \
                        -v "$WORKSPACE/app":/app \
                        -w /app \
                        node:18 bash -c "ls -la && npm install && npm test"
                '''
            }
        }
    }
}
