## Deploy Super Mario Game on AWS EKS (Elastic Kubernetes Service) ##

### Introduction ###

This project is to deploy a Super Mario Game on AWS EKS (Elastic Kubernetes Service). The Super Mario Game is a web application that is developed by using Python Flask framework. The game is to collect coins and avoid obstacles. The game is deployed on AWS EKS (Elastic Kubernetes Service) with 3 nodes. 

# Requirements 

- AWS Account
- AWS CLI
- AWS EKSCTL 
- AWS IAM Authenticator with admin access 
- Kubectl
- Git

# Steps 
1. Create mario directory and change directory to mario directory. 
```
shell> mkdir mario && cd mario
```
2. Git clone the Super Mario Game repository and also change directory to mario-eks directory. 
```
shell> git clone https://github.com/Amul-Thantharate/mario-eks.git 
```
3. Directory structure should look like this. 
``` 
shell> tree
.
└── mario-eks
    | -- readme.md
    | -- deployment.yaml
    | -- service.yaml
    | -- eksctl-config.yaml
    | -- Images
```
