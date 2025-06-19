pipeline {
    agent any

    environment {
        NVM_DIR = "${HOME}/.nvm"
    }

    stages {
        stage('Checkout código') {
            steps {
                checkout scm
            }
        }

        stage('Test paralelos Node.js') {
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

        echo "🔧 Ejecutando tests ecnnn Node.js v${version}"
        npm install
        npm test
    """
}
