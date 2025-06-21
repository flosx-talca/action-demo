pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Test con Docker Node 18') {
            steps {
                sh '''
                    docker run --rm -v "$WORKSPACE":/app -w /app node:18 bash -c "npm install && npm test"
                '''
            }
        }
    }
}
