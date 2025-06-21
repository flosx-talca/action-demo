pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Preparar carpeta app') {
            steps {
                sh '''
                    mkdir -p app
                    cp -r package.json package-lock.json src tests app/
                '''
            }
        }

        stage('Test en Docker') {
            steps {
                sh '''
                    docker run --rm \
                        -v "$WORKSPACE/app":/app \
                        -w /app \
                        node:18 bash -c "ls -la && npm install && npm test"
                '''
            }
        }
    }
}
