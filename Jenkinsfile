pipeline {
    agent none

    stages {
        stage('Test paralelos Node.js') {
            parallel {
                stage('Node 18') {
                    agent {
                        docker { image 'node:18' }
                    }
                    steps {
                        sh 'node -v && npm install && npm test'
                    }
                }
                stage('Node 20') {
                    agent {
                        docker { image 'node:20' }
                    }
                    steps {
                        sh 'node -v && npm install && npm test'
                    }
                }
                stage('Node 22') {
                    agent {
                        docker { image 'node:22' }
                    }
                    steps {
                        sh 'node -v && npm install && npm test'
                    }
                }
            }
        }
    }
}
