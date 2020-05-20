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
Run the **create-network-stack.sh** script passing in the appropriate parameters to create the VPC, Subnets, Routes and Control plane security group The **cluster-network-params.json** is the parameter file

#### Create the EKS cluster
Run the **create-cluster-stack.sh** script passing in the appropriate parameters to create the EKS cluster. The **cluster-params.json** is the parameter file

#### Create the Worker nodes
Run the **create-worker-stack.sh** script passing in the appropriate parameters. to create worker nodes and joins them to the clister. It also creates the security group for the nides and the appropriate IAM role and policy. The **cluster-params.json** is the parameter file

## Other files

-  [deploy-rolling.yaml])(https://github.com/bolfak/nginxhello/blob/master/deploy-rolling.yaml) - This is the deployment config file
-  [aws-auth-cm.yaml])(https://github.com/bolfak/nginxhello/blob/master/aws-auth-cm.yaml) - This is the kubectl role mapping config


