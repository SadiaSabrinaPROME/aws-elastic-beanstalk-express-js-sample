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
            sh 'npm list --depth=0 > dependency-report.txt || true'
            archiveArtifacts artifacts: 'dependency-report.txt', fingerprint: true            
        }

        success {
            echo 'Pipeline completed successfully.'
        }

        failure {
            echo 'Pipeline failed. Check the build logs.'
        }
    }
}
