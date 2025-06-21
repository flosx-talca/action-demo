pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Verificar estructura y npm install') {
            steps {
                sh '''
                    echo "Listado carpeta workspace en el contenedor:"
                    docker run --rm -v "$WORKSPACE":/app -w /app node:18 bash -c "ls -la /app"
                    
                    echo "Intentando npm install en /app"
                    docker run --rm -v "$WORKSPACE":/app -w /app node:18 bash -c "npm install"
                '''
            }
        }
    }
}
