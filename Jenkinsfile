pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Test con Node 22') {
            steps {
                sh '''
                    docker run --rm \
                        -v "$WORKSPACE":/app \
                        -w /app \
                        node:22 bash -c "ls -la && npm install && npm test"
                '''
            }
        }
    }
}
