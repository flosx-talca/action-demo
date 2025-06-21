pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verificar estructura en host') {
            steps {
                sh '''
                    echo "📁 Listado desde Jenkins:"
                    ls -la /var/jenkins_home/workspace/app-node
                    echo "📝 Mostrando package.json:"
                    cat /var/jenkins_home/workspace/app-node/package.json || echo "❌ No encontrado"
                '''
            }
        }

        stage('Test en paralelo') {
            parallel {
                stage('Node 18') {
                    steps {
                        sh '''
                            echo "🚀 Ejecutando tests en Node 18..."
                            docker run --rm \
                                -v /var/jenkins_home/workspace/app-node:/app \
                                -w /app \
                                node:18 bash -c "
                                    echo '📁 Archivos dentro del contenedor:';
                                    ls -la /app;
                                    echo '📝 Mostrando package.json:';
                                    cat /app/package.json || echo '❌ No encontrado';
                                    npm install && npm test
                                "
                        '''
                    }
                }
                stage('Node 20') {
                    steps {
                        sh '''
                            echo "🚀 Ejecutando tests en Node 20..."
                            docker run --rm \
                                -v /var/jenkins_home/workspace/app-node:/app \
                                -w /app \
                                node:20 bash -c "
                                    npm install && npm test
                                "
                        '''
                    }
                }
                stage('Node 22') {
                    steps {
                        sh '''
                            echo "🚀 Ejecutando tests en Node 22..."
                            docker run --rm \
                                -v /var/jenkins_home/workspace/app-node:/app \
                                -w /app \
                                node:22 bash -c "
                                    npm install && npm test
                                "
                        '''
                    }
                }
            }
        }
    }
}
