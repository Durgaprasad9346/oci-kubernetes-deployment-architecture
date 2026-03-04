# Deploying a Web Application on Oracle Kubernetes Engine (OKE)

## Overview

This repository demonstrates how to deploy a containerized web application on **Oracle Kubernetes Engine (OKE)** using Kubernetes manifests. The implementation showcases how applications running inside a Kubernetes cluster can be exposed to external users through an **Ingress Controller and OCI Load Balancer**.

Oracle Kubernetes Engine (OKE) is a fully managed Kubernetes service provided by Oracle Cloud Infrastructure (OCI) that simplifies the deployment, management, and scaling of containerized workloads.

This project provides a basic reference implementation for deploying a web application using Kubernetes resources such as Deployments, Services, and Ingress.

---

## Architecture Overview

![OKE Web Application Architecture](architecture/oke-webapp-architecture.png)

The architecture represents a common deployment pattern used for hosting web applications on Kubernetes.

External users access the application through an OCI Load Balancer. Traffic is routed to an **Ingress Controller** running inside the Kubernetes cluster. The ingress controller forwards requests to a Kubernetes service, which then routes traffic to the application pods running across worker nodes.

### Traffic Flow

Internet
│
OCI Load Balancer
│
Ingress Controller
│
Kubernetes Service (ClusterIP)
│
Oracle Kubernetes Engine (OKE) Cluster
├── Worker Node 1
│   └── Web Application Pod (NGINX)
└── Worker Node 2
└── Web Application Pod (NGINX)

This design provides scalability, high availability, and simplified traffic management for containerized applications.

---

## Components Used

The following technologies are used in this implementation:

**Oracle Cloud Infrastructure (OCI)**
Provides the underlying cloud infrastructure including networking and load balancing.

**Oracle Kubernetes Engine (OKE)**
Managed Kubernetes service used to run containerized workloads.

**Kubernetes Deployment**
Defines the desired state of the web application pods and ensures that the required number of replicas are running.

**Kubernetes Service (ClusterIP)**
Provides internal communication within the cluster and exposes the application to the ingress controller.

**Ingress Controller**
Handles external HTTP/HTTPS traffic and routes it to the appropriate Kubernetes service.

**NGINX Container Image**
Used as a simple web application for demonstration purposes.

---

## Repository Structure

architecture/
Contains architecture diagrams that illustrate the deployment model.

kubernetes-manifests/
Contains Kubernetes YAML manifests used to deploy and expose the application.

README.md
Project documentation describing the architecture and deployment workflow.

---

## Kubernetes Resources Included

### Deployment

The deployment creates multiple replicas of an NGINX web application pod. Kubernetes ensures that the defined number of replicas are always running.

File:
kubernetes-manifests/deployment.yaml

---

### Service

The service exposes the application internally within the cluster. The ingress controller forwards traffic to this service.

File:
kubernetes-manifests/service.yaml

Service Type:
ClusterIP

---

### Ingress

The ingress resource routes external HTTP traffic to the application service.

File:
kubernetes-manifests/ingress.yaml

Ingress allows applications running in the cluster to be accessed using a domain name or external endpoint.

---

## Deployment Steps

Apply the Kubernetes manifests to deploy the application.

Deploy the application pods:

kubectl apply -f kubernetes-manifests/deployment.yaml

Create the internal service:

kubectl apply -f kubernetes-manifests/service.yaml

Create the ingress resource:

kubectl apply -f kubernetes-manifests/ingress.yaml

---

## Verification

Check whether the pods are running:

kubectl get pods

Verify the service:

kubectl get svc

Check ingress configuration:

kubectl get ingress

Once the ingress and load balancer are provisioned, the application can be accessed through the external endpoint.

---

## Learning Outcomes

Through this project, the following concepts can be understood:

* Deploying containerized applications on Oracle Kubernetes Engine
* Managing application replicas using Kubernetes Deployments
* Exposing applications internally using Kubernetes Services
* Routing external traffic using Kubernetes Ingress
* Understanding how OCI load balancers integrate with Kubernetes networking

---

## Real World Use Case

Modern cloud-native applications are often deployed using container orchestration platforms such as Kubernetes. Oracle Kubernetes Engine provides a scalable and managed environment for running these workloads on Oracle Cloud Infrastructure.

This architecture can serve as a starting point for deploying web applications, APIs, and microservices in OCI while leveraging Kubernetes for scalability and reliability.

---

## Author

Durga Prasad
Oracle ACE Program – Apprentice
