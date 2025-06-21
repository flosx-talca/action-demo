pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('npm install') {
      steps {
        sh '''
          echo "Listado carpeta app-node en contenedor:"
          docker run --rm -v "$WORKSPACE":/app -w /app node:18 bash -c "ls -la /app"
          echo "Ejecutando npm install"
          docker run --rm -v "$WORKSPACE":/app -w /app node:18 bash -c "npm install"
        '''
      }
    }
  }
}
