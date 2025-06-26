pipeline {
    agent {
        docker {
            image 'node:18'
            args '-v /tmp:/tmp'
        }
    }

    stages {
        stage('Instalar dependencias') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
    }
}
