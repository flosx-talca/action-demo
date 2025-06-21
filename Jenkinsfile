pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test en paralelo') {
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
