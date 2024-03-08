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

