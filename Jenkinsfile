pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Build the Docker image
                    sh 'export PATH=$PATH:/usr/local/bin && docker build -t ci-cd-demo .'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run tests using pytest inside the container
                    sh 'export PATH=$PATH:/usr/local/bin && docker run --rm ci-cd-demo pytest'
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    // Scan the Docker image for vulnerabilities with Trivy
                    sh 'export PATH=$PATH:/usr/local/bin && docker run --rm aquasec/trivy image ci-cd-demo'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Run the Docker container
                    sh 'export PATH=$PATH:/usr/local/bin && docker run -d -p 8080:8080 --name ci-cd-demo-container ci-cd-demo'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed!'
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
