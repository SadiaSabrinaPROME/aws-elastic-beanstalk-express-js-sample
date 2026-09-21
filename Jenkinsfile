pipeline {
    agent any
    

    stages {
        stage('Install Dependencies') {
            steps {
                echo 'Installing Node.js dependencies...'
                sh 'npm ci'
            }
        }

        stage('Test') {
            steps {
                echo 'Running application tests...'
                sh 'npm test'
            }
        }
        stage('Security Scan') {
           steps {
               echo 'Scanning dependencies for vulnerabilities...'
               sh 'npm audit --audit-level=high'
           }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }

        success {
            echo 'Pipeline completed successfully.'
        }

        failure {
            echo 'Pipeline failed. Check the build logs.'
        }
    }
}
