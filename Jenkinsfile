pipeline {
    agent none

    stages {
        stage('Test en múltiples versiones de Node.js') {
            matrix {
                axes {
                    axis {
                        name 'NODE_VERSION'
                        values '18', '20', '22'
                    }
                }

                stages {
                    stage('Instalar dependencias') {
                        agent {
                            docker {
                                image "node:${NODE_VERSION}"
                                args '-v /tmp:/tmp'
                            }
                        }
                        steps {
                            echo "📦 Instalando dependencias en Node.js ${NODE_VERSION}"
                            sh 'npm ci'
                        }
                    }

                    stage('Ejecutar pruebas') {
                        steps {
                            echo "🧪 Ejecutando pruebas en Node.js ${NODE_VERSION}"
                            sh 'npm test'
                        }
                    }
                }
            }
        }
    }
}


