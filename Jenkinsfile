pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'export PATH=$PATH:/usr/local/bin && docker build -t ci-cd-demo .'
                }
            }
        }
    }
}
