pipeline {
  agent any

  environment {
    NODE_ENV = 'development'
  }

  stages {
    stage('Verificar versión de Node y npm') {
      steps {
        sh '''
          echo "Node version:"
          node -v

          echo "npm version:"
          npm -v
        '''
      }
    }

    stage('Instalación de dependencias') {
      steps {
        sh 'npm ci || npm install'
      }
    }

    stage('Ejecución de tests') {
      steps {
        sh 'npm test'
      }
    }

    stage('Final') {
      steps {
        echo 'Pipeline Node.js finalizado correctamente.'
      }
    }
  }
}
