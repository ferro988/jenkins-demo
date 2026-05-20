pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo "Building local branch"
            }
        }
        stage('Install') {
            steps {
                sh 'npm install || true'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Package') {
            steps {
                sh 'tar -czf app.tar.gz app.js package.json'
                archiveArtifacts artifacts: 'app.tar.gz', fingerprint: true
            }
        }
    }
    post {
        success { echo '✅ Pipeline succeeded' }
        failure { echo '❌ Pipeline failed — check console output' }
        always  { echo "Finished build #${env.BUILD_NUMBER}" }
    }
}
