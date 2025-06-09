pipeline {
    agent { label '2023Q1' }

    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: '2025Q1', url: 'https://github.com/Shubhamtapkir29/2025.git'
            }
        }

        stage('Clean Deploy Directory') {
            steps {
                sh '''
                echo "🧹 Cleaning $DEPLOY_DIR on arpita-slave"
                sudo rm -rf ${DEPLOY_DIR}/*
                '''
            }
        }

        stage('Deploy to Apache') {
            steps {
                sh '''
                echo "🚀 Deploying to Apache on arpita-slave"
                sudo cp -r * ${DEPLOY_DIR}/
                sudo chmod -R 755 ${DEPLOY_DIR}
                sudo systemctl restart httpd
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Deployment on 'arpita-slave' successful!"
        }
        failure {
            echo "❌ Deployment failed. Check logs on '2023Q1'."
        }
    }
}
