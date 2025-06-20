pipeline {
    agent any

    environment {
        NVM_DIR = "${HOME}/.nvm"
    }

    stages {
        stage('Validar rama') {
            when {
                not {
                    anyOf {
                        branch 'main'
                        branch 'ci'
                    }
                }
            }
            steps {
                echo "⛔ Este pipeline solo se ejecuta en las ramas main o ci. Rama actual: ${env.BRANCH_NAME}"
                error("Abortado: Rama no permitida")
            }
        }

        stage('Checkout código') {
            when {
                anyOf {
                    branch 'main'
                    branch 'ci'
                }
            }
            steps {
                checkout scm
            }
        }

        stage('Test paralelos Node.js') {
            when {
                anyOf {
                    branch 'main'
                    branch 'ci'
                }
            }
            parallel {
                stage('Node 18') {
                    steps {
                        script {
                            runTestsWithNode('18')
                        }
                    }
                }
                stage('Node 20') {
                    steps {
                        script {
                            runTestsWithNode('20')
                        }
                    }
                }
                stage('Node 22') {
                    steps {
                        script {
                            runTestsWithNode('22')
                        }
                    }
                }
            }
        }
    }
}

def runTestsWithNode(String version) {
    sh """
        export NVM_DIR="\$HOME/.nvm"
        [ -s "\$NVM_DIR/nvm.sh" ] && . "\$NVM_DIR/nvm.sh"

        nvm install ${version}
        nvm use ${version}

        echo "🔧 Ejecutando test en Node.js v${version}"
        npm install
        npm test
    """
}
