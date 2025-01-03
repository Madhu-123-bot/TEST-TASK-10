# Static Website Hosting with Amazon S3 and Automated Deployment Using Jenkins

This project demonstrates hosting a static website on **Amazon S3** and automating the deployment process using a **Jenkins Pipeline**. The pipeline pulls website files from a **GitHub repository** and deploys them to an S3 bucket, ensuring an efficient and seamless CI/CD workflow.

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Technologies Used](#technologies-used)
4. [Setup Instructions](#setup-instructions)
5. [Pipeline Stages](#pipeline-stages)
6. [Verification](#verification)
7. [Future Enhancements](#future-enhancements)
8. [License](#license)

---

## Overview

This project simplifies the process of hosting static websites using **Amazon S3**. With the integration of **Jenkins**, changes pushed to a GitHub repository can be automatically deployed to the live website hosted on S3. This project is a real-world solution for managing content delivery efficiently while adhering to CI/CD principles.

---

## Features

- Static website hosting on Amazon S3.
- Fully automated deployment using a Jenkins pipeline.
- GitHub integration for version control.
- Supports deployment on any changes committed to the repository.
- Extendable for use with **AWS CloudFront** for better performance and HTTPS support.

---

## Technologies Used

- **Amazon S3** for static website hosting.
- **Jenkins** for CI/CD automation.
- **AWS CLI** for managing AWS services from the command line.
- **GitHub** for version control and code repository.
- **EC2 Ubuntu** instance for hosting Jenkins.

---

## Setup Instructions

### 1. Prerequisites

- An AWS account with permissions to manage S3 and IAM.
- A GitHub repository with your static website files (HTML, CSS, JS).
- An EC2 Ubuntu instance with Jenkins installed.

### 2. Create an S3 Bucket

1. Log in to the AWS Console.
2. Create an S3 bucket with a globally unique name.
3. Enable **Static website hosting** in the bucket properties.
4. Set `index.html` as the index document.

### 3. Configure EC2 Instance

1. Install **AWS CLI**:
   ```bash
   sudo apt update
   sudo apt install awscli -y (Refer Official Documentation)
   aws configure

2.Install Jenkins and required plugins:
    a.Install Jenkins and start it (sudo apt install jenkins -y).(Refer Official Documentation)
    b.Install AWS SDK and Amazon EC2 plugin from Jenkins Plugin Manager

### 4. Create a Jenkins Job

1.Create a Pipeline Job in Jenkins.
2.Use the pipeline script in Pipeline Stages.

### 5. Pipeline Stages
The Jenkins pipeline performs the following stages:

1.Checkout Code:
Pulls the latest code from the specified GitHub repository.
2.Sync with S3:
Uses aws s3 sync to upload static website files to the S3 bucket.
3.Invalidate CloudFront Cache (Optional):
Invalidate CloudFront cache after deployment to ensure updated content.

### 6. Verification

1.Navigate to your S3 bucket's Static Website Hosting URL.
2.Verify that the website displays correctly.
3.Any changes pushed to the GitHub repository will automatically trigger the Jenkins pipeline and update the website.

### 7. Future Enhancements

1.Use CloudFront for faster delivery and HTTPS support.
2.Implement error handling in Jenkins pipeline stages.
3.Add automated testing before deployment.

