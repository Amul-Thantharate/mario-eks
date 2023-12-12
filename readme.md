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
4. Run the following command to create EKS cluster. 
``` 
shell> eksctl create cluster -f eksctl-config.yaml
```
5. Run the following command to check the status of EKS cluster. 
```
shell> aws eks describe-cluster --name mario-cluster --query "cluster.{Name: name, Status: status, Endpoint: endpoint, Version: version, DateOfCreation: createdAt}" --output table
```
6. Run the following command to update the kubeconfig file. 
```
shell> aws eks --region us-east-1 update-kubeconfig --name mario-cluster
```
7. Run the following command to apply the deployment.yaml file. 
```
shell> kubectl apply -f deployment.yaml
``` 
8. Run the following command to apply the service.yaml file. 
```
shell> kubectl apply -f service.yaml
```
9. Verify the service with the “kubectl describe service” command: 
```
shell> kubectl describe service mario-service
```
10. Destroy the EKS cluster with the following command. 
```
shell> eksctl delete cluster --name mario-cluster
```

# References
- AWS EKSCTL: https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html
- AWS EKS: https://aws.amazon.com/eks/
- AWS IAM Authenticator: https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html
- Kubectl: https://kubernetes.io/docs/tasks/tools/install-kubectl/

