# OCI Kubernetes Deployment Architecture

## Overview
This repository demonstrates a reference architecture for deploying containerized workloads on Oracle Cloud Infrastructure (OCI) using Oracle Kubernetes Engine (OKE).

The project includes Kubernetes manifests and architecture diagrams that illustrate how applications can be deployed and exposed using OCI networking and load balancing.

## Architecture

The architecture consists of:

Internet
│
OCI Load Balancer
│
Ingress Controller
│
OKE Cluster
├── Worker Node
│   └── NGINX Pod
└── Worker Node
    └── NGINX Pod

## Components Used

- Oracle Cloud Infrastructure (OCI)
- Oracle Kubernetes Engine (OKE)
- Kubernetes Deployment
- Kubernetes Service (LoadBalancer)
- NGINX container image

## Deployment Steps

Apply Kubernetes manifests:

kubectl apply -f kubernetes-manifests/deployment.yaml
kubectl apply -f kubernetes-manifests/service.yaml

Verify resources:

kubectl get pods
kubectl get svc

## Learning Outcome

This project demonstrates how Oracle Kubernetes Engine integrates with Kubernetes networking and OCI load balancers to expose containerized workloads.

## Repository Structure

architecture/
Contains architecture diagrams

kubernetes-manifests/
Contains Kubernetes deployment and service manifests
