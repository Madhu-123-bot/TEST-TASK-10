pipeline {
    agent any

    environment {
        AWS_REGION = 'ap-south-1'               // Replace with your region
        S3_BUCKET_NAME = 'mmy-website-bucket'   // Replace with your S3 bucket
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Madhu-123-bot/TEST-TASK-10.git'
            }
        }

        stage('Sync with S3') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'aws-s3-credentials', usernameVariable: 'AWS_ACCESS_KEY_ID', passwordVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                    script {
                        sh '''
                            aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID
                            aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY
                            aws configure set region $AWS_REGION
                            aws s3 sync ./ s3://$S3_BUCKET_NAME --exclude ".git/*"
                        '''
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Deployment finished.'
        }
    }
}
