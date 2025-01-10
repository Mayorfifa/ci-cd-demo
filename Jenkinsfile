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
                    sh 'docker run ci-cd-demo pytest'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'docker run -d -p 8080:8080 ci-cd-demo'
                }
            }
        }
    }
}
