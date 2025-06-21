pipeline {
    agent any

    stages {
        stage('Checkout código') {
            steps {
                checkout scm
            }
        }

        stage('Test paralelos Node.js') {
            parallel {
                stage('Node 18') {
                    agent {
                        docker { image 'node:18' }
                    }
                    steps {
                        sh '''
                            echo "🔧 Test con Node 18"
                            npm install
                            npm test
                        '''
                    }
                }
                stage('Node 20') {
                    agent {
                        docker { image 'node:20' }
                    }
                    steps {
                        sh '''
                            echo "🔧 Test con Node 20"
                            npm install
                            npm test
                        '''
                    }
                }
                stage('Node 22') {
                    agent {
                        docker { image 'node:22' }
                    }
                    steps {
                        sh '''
                            echo "🔧 Test con Node 22"
                            npm install
                            npm test
                        '''
                    }
                }
            }
        }
    }
}
