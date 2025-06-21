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
                            docker run --rm -v "$WORKSPACE":/workspace -w /workspace/action-demo node:18 bash -c "
                                ls -la /workspace/action-demo &&
                                npm install &&
                                npm test
                            "
                        '''
                    }
                }
                stage('Node 20') {
                    steps {
                        sh '''
                            docker run --rm -v "$WORKSPACE":/workspace -w /workspace/action-demo node:20 bash -c "
                                ls -la /workspace/action-demo &&
                                npm install &&
                                npm test
                            "
                        '''
                    }
                }
                stage('Node 22') {
                    steps {
                        sh '''
                            docker run --rm -v "$WORKSPACE":/workspace -w /workspace/action-demo node:22 bash -c "
                                ls -la /workspace/action-demo &&
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
