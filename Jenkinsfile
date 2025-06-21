pipeline {
    agent any

    stages {
        stage('Verificar estructura') {
            steps {
                sh '''
                    docker run --rm -v "$WORKSPACE":/workspace -w /workspace node:18 bash -c "
                        echo 'Contenido en /workspace:' &&
                        ls -la /workspace &&
                        echo 'Contenido en /workspace/action-demo:' &&
                        ls -la /workspace/action-demo &&
                        echo 'Contenido en /workspace/action-demo/src:' &&
                        ls -la /workspace/action-demo/src
                    "
                '''
            }
        }
    }
}
