Example containerized application that uses Zuul (Netflix OSS) for edge routing a simple Spring Boot application and host in Azure Kubernetes Service (AKS). 

NOTE: This repo can be used a loose guide for getting started, however, I did not put too much effort into precisely documenting each step. I loosely document the steps for AKS as well. Please feel free to add and submit a pull request if you have the time/desire. 

The following guides were used as cheat sheets:

Building a micrservice architecture with Spring Boot and Docker (four part series):

https://www.3pillarglobal.com/insights/building-a-microservice-architecture-with-spring-boot-and-docker-part-i

Dockerizing a Spring Boot application:

http://www.baeldung.com/dockerizing-spring-boot-application

Skunkworks project for running containerized Zuul:

https://github.com/Netflix-Skunkworks/zerotodocker

Deploying an AKS cluster - This step assumes you already have Azure CLI installed and have access to an Azure Subscription:

#create vnet
az group create -n <RG-Name> -l eastus

#create AKS cluster
az aks create -g <RG-Name> -n <Cluster-Name> --node-count 2 --ssh-key-value ~/.ssh/id_rsa.pub