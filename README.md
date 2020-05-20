# Udacity Cloud DevOps Nanaodegree Capstone

A Jenkins CI/D pipeline for a contanerized application using the rolling deployment model

## Technologies

- Amazon Elastic Kubernetes Service 
- Jenkins for CI/CD
- AWS Cloudformatyion for creating infrastructure
- Docker
- Kubectl / eksctl

## Implementation

Due to time constraints, i could not build a new application for the purpose of tyhis capstone. I used the nginxhello sample for this purpose

### Set up the Jenkins Server

I installed Jenkins on an EC2 instance and installed the necessary plugins - Blue Ocean and Docker. I also installed Tidy for linting HTML files. I installed these manually as they won't be part of the pipeline.

### Set up the infrastructure

#### Create the VPC
