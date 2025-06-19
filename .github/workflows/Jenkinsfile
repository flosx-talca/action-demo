pipeline {
    agent any

    environment {
        NVM_DIR = "${HOME}/.nvm"
        NODE_VERSION = "18"
    }

    stages {
        stage('Checkout código') {
            steps {
                checkout scm
            }
        }

        stage('Configurar Node y ejecutar tests') {
            steps {
                script {
                    sh """
                        export NVM_DIR="\$HOME/.nvm"
                        [ -s "\$NVM_DIR/nvm.sh" ] && . "\$NVM_DIR/nvm.sh"

                        nvm install ${NODE_VERSION}
                        nvm use ${NODE_VERSION}

                        npm install
                        npm test
                    """
                }
            }
        }
    }
}
