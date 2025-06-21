pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verificar estructura') {
            steps {
                sh '''
                    echo "📁 Listado desde Jenkins:"
                    ls -la $WORKSPACE
                    echo "📝 Mostrando package.json:"
                    cat $WORKSPACE/package.json
                '''
            }
        }

        stage('Test en paralelo') {
            parallel {
                stage('Node 18') {
                    steps {
                        sh '''
                            echo "🚀 Test con Node 18"
                            docker run --rm \
                                -v "$WORKSPACE":/app \
                                -w /app \
                                node:18 bash -c "npm install && npm test"
                        '''
                    }
                }

                stage('Node 20') {
                    steps {
                        sh '''
                            echo "🚀 Test con Node 20"
                            docker run --rm \
                                -v "$WORKSPACE":/app \
                                -w /app \
                                node:20 bash -c "npm install && npm test"
                        '''
                    }
                }

                stage('Node 22') {
                    steps {
                        sh '''
                            echo "🚀 Test con Node 22"
                            docker run --rm \
                                -v "$WORKSPACE":/app \
                                -w /app \
                                node:22 bash -c "npm install && npm test"
                        '''
                    }
                }
            }
        }
    }
}
