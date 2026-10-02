cat > Jenkinsfile <<'EOF'
pipeline {
    agent any

    environment {
        IMAGE_NAME = "week9-jenkins-docker"
        CONTAINER_NAME = "week9-app"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'docker build -t ${IMAGE_NAME}:${BUILD_NUMBER} .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated test...'
                sh 'docker run --rm ${IMAGE_NAME}:${BUILD_NUMBER} nginx -t'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running Trivy security scan...'
                sh '''
                    trivy image \
                    --scanners vuln \
                    --pkg-types os \
                    --skip-db-update \
                    --format table \
                    -o security-scan-report.txt \
                    ${IMAGE_NAME}:${BUILD_NUMBER}
                '''
            }
        }

        stage('Package') {
            steps {
                echo 'Docker image packaged successfully.'
                sh 'docker images ${IMAGE_NAME}'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'security-scan-report.txt',
                             allowEmptyArchive: true
        }
    }
}
EOF
