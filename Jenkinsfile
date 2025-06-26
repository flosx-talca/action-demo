pipeline {
    agent any

    stages {
        stage('Clonar') {
            steps {
                git 'https://github.com/flosx-talca/action-demo'
            }
        }

        stage('Listar archivos') {
            steps {
                sh 'ls -la'
                sh 'ls -la app/'
            }
        }

        stage('Instalar dependencias') {
            steps {
                sh '''
                docker run --rm -v $(pwd):/app -w /app/app node:18 bash -c "npm ci"
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                docker run --rm -v $(pwd):/app -w /app/app node:18 bash -c "npm test"
                '''
            }
        }
    }
}
