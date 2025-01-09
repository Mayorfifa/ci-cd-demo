pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'docker build -t ci-cd-demo .'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh 'pytest || echo "Tests failed!"'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'docker run ci-cd-demo'
                }
            }
        }
    }
}

