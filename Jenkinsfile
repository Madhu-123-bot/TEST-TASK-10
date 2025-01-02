pipeline {
    agent any
    
    environment {
        AWS_REGION = 'ap-south-1'               // AWS Region 
        S3_BUCKET_NAME = 'mmy-website-bucket'    // Your S3 Bucket name
    }
    
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Madhu-123-bot/TEST-TASK-10.git' // Your GitHub repo
            }
        }
        
        stage('Sync with S3') {
            steps {
                script {
                    // Sync the code to S3
                    sh '''
                        aws s3 sync ./ s3://$S3_BUCKET_NAME --exclude ".git/*"
                    '''
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

