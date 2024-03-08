# Chiken Disease Classification Project

## Overview
This project aims to classify chicken diseases using convolutional neural networks (CNN). It provides a web interface to upload chicken images and get predictions on potential diseases.

## Workflows

1. Update config.yaml
2. Update secrets.yaml [Optional]
3. Update params.yaml
4. Update the entity
5. Update the configuration manager in src config
6. Update the components
7. Update the pipeline 
8. Update the main.py
9. Update the dvc.yaml


## Getting Started

### Prerequisites
- Conda environment
- Python 3.8 or higher

### Installation Steps

1. **Clone the Repository**

    ```bash
   https://github.com/mbabeykoon/ChikenDiseaseClassification.git
    ```

2. **Create and Activate Conda Environment**

    ```bash
    conda create -n cnncls python=3.8 -y
    conda activate cnncls
    ```

3. **Install the Requirements**

    ```bash
    pip install -r requirements.txt
    ```

4. **Run the Application**

    ```bash
    python app.py
    ```

    Open your local host in the browser to access the application.

## DVC Commands

- Initialize DVC: `dvc init`
- Reproduce DVC pipeline: `dvc repro`
- Visualize DVC pipeline: `dvc dag`

  
# AWS CI/CD Deployment with GitHub Actions

This guide outlines the process for deploying a Docker-based application on AWS EC2, utilizing AWS ECR for Docker image storage, and orchestrating it through GitHub Actions.

## Prerequisites

- AWS Account
- Docker installed on your local machine
- GitHub Account

## Steps

### 1. AWS Console Setup

#### IAM User Creation

1. Login to the AWS console.
2. Navigate to IAM service and create a new user with programmatic access.
3. Attach the following policies for necessary access:
   - `AmazonEC2ContainerRegistryFullAccess`
   - `AmazonEC2FullAccess`

#### ECR Repository Creation

1. Go to the Amazon ECR service and create a new repository.
   - Note down the URI (e.g., `381492009513.dkr.ecr.us-east-2.amazonaws.com/chicken`).

#### EC2 Instance Setup

1. Launch an EC2 instance (Ubuntu recommended).
2. SSH into your instance after it's up and running.

##### Docker Installation on EC2

```bash
sudo apt-get update -y
sudo apt-get upgrade -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```
# Configuring EC2 as a Self-Hosted Runner for GitHub Actions

## Configure EC2 as Self-Hosted Runner

To enhance your CI/CD pipeline, you can use your AWS EC2 instance as a self-hosted runner. This allows for more control over the environment where your GitHub Actions workflows run.

### Steps:

1. Navigate to your GitHub repository's Settings.
2. Go to Actions > Runners.
3. Click on "New self-hosted runner".
4. Select the operating system of your EC2 instance.
5. Follow the provided instructions to download, configure, and start the runner on your EC2 instance.

    These steps typically involve executing shell commands on your EC2 instance to download the runner application, configure it with your repository, and start the runner service.

##  Setting Up GitHub Secrets

To securely store and use sensitive information in your GitHub Actions workflows, you should use GitHub Secrets.

### Required Secrets:

You'll need to set up the following secrets in your GitHub repository:

- `AWS_ACCESS_KEY_ID`: Your AWS IAM user's access key ID.
- `AWS_SECRET_ACCESS_KEY`: Your AWS IAM user's secret access key.
- `AWS_REGION`: The AWS region where your resources are located (e.g., `us-east-1`).
- `AWS_ECR_LOGIN_URI`: The login URI for your AWS ECR repository (e.g., `566373416292.dkr.ecr.ap-south-1.amazonaws.com`).
- `ECR_REPOSITORY_NAME`: The name of your ECR repository where the Docker images will be stored (e.g., `simple-app`).

### How to Set Secrets:

1. In your GitHub repository, navigate to Settings.
2. Click on Secrets in the left sidebar, then choose Actions.
3. Click on "New repository secret" to add each of the above secrets.

Ensure these secrets match the credentials and resource names you've set up in AWS. These secrets will be used in your GitHub Actions workflows to interact with AWS services securely.

