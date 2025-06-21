pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', 
                  branches: [[name: '*/main']], 
                  userRemoteConfigs: [[url: 'https://github.com/flosx-talca/action-demo.git']]])
            }
        }

        stage('Verificar estructura') {
            steps {
                sh '''
                    echo "Listado de archivos en workspace:"
                    ls -la $WORKSPACE
                    echo "Contenido detallado:"
                    ls -laR $WORKSPACE
                    echo "Contenido de package.json (si existe):"
                    if [ -f $WORKSPACE/package.json ]; then
                        cat $WORKSPACE/package.json
                    else
                        echo "package.json no encontrado"
                    fi
                '''
            }
        }

        stage('Tests en paralelo') {
            parallel {
                stage('Node 18') {
                    steps {
                        sh '''
                            docker run --rm -v "$WORKSPACE":/app -w /app node:18 bash -c "
                                npm install &&
                                npm test
                            "
                        '''
                    }
                }
                stage('Node 20') {
                    steps {
                        sh '''
                            docker run --rm -v "$WORKSPACE":/app -w /app node:20 bash -c "
                                npm install &&
                                npm test
                            "
                        '''
                    }
                }
                stage('Node 22') {
                    steps {
                        sh '''
                            docker run --rm -v "$WORKSPACE":/app -w /app node:22 bash -c "
                                npm install &&
                                npm test
                            "
                        '''
                    }
                }
            }
        }
    }
}
