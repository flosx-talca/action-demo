pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Prueba básica en Node') {
            steps {
                sh '''
                    docker run --rm -v "$WORKSPACE":/app -w /app node:18 bash -c "ls -la && node -v"
                '''
            }
        }
    }
}
