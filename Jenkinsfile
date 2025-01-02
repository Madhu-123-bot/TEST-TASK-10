pipeline {
    agent any
    
    environment {
        AWS_REGION = 'us-west-2'               // AWS Region
        S3_BUCKET_NAME = 'my-website-bucket'   // Your S3 Bucket name
    }
    
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Madhu-123-bot/TEST-TASK-10.git'
            }
        }
        
        stage('Sync with S3') {
            steps {
                script {
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
