# Deploying a Web Application on Oracle Kubernetes Engine (OKE)

## Overview

This repository demonstrates a reference implementation for deploying a containerized web application on **Oracle Kubernetes Engine (OKE)**, a managed Kubernetes service provided by Oracle Cloud Infrastructure (OCI).

The objective of this project is to illustrate how Kubernetes workloads can be deployed and exposed to external users using OCI networking capabilities. By leveraging OKE, developers and platform engineers can run scalable containerized applications while offloading cluster management responsibilities to OCI.

This repository contains Kubernetes manifests and architecture references that describe how a simple web application can be deployed and exposed using Kubernetes services integrated with OCI infrastructure.

---

## Oracle Kubernetes Engine (OKE)

**Oracle Kubernetes Engine (OKE)** is a fully managed Kubernetes service that simplifies the deployment, management, and scaling of containerized applications on Oracle Cloud Infrastructure.

OKE provides several benefits for organizations adopting cloud-native architectures:

* Managed Kubernetes control plane
* Automated cluster scaling and management
* Native integration with OCI networking and load balancing
* High availability and fault tolerance
* Support for standard Kubernetes tools such as kubectl and Helm

By using OKE, teams can focus on building and deploying applications while OCI handles cluster management and infrastructure reliability.

---

## Architecture Overview

The architecture for this project represents a typical Kubernetes application deployment model on Oracle Cloud Infrastructure.

External users access the web application through an OCI load balancer created automatically when a Kubernetes Service of type **LoadBalancer** is deployed. The load balancer routes traffic to services running inside the Oracle Kubernetes Engine cluster.

Inside the cluster, application pods are scheduled across worker nodes, ensuring scalability and high availability.

### High-Level Architecture

Internet
│
OCI Load Balancer
│
Kubernetes Service (LoadBalancer)
│
Oracle Kubernetes Engine (OKE) Cluster
├── Worker Node 1
│   └── Web Application Pod (NGINX)
└── Worker Node 2
└── Web Application Pod (NGINX)

This design enables external users to access applications securely while allowing Kubernetes to manage application scaling and availability.

---

## Components Used

This implementation references the following technologies:

* **Oracle Cloud Infrastructure (OCI)** – Cloud platform providing networking and compute resources
* **Oracle Kubernetes Engine (OKE)** – Managed Kubernetes service used to host containerized workloads
* **Kubernetes Deployment** – Defines and manages application pods
* **Kubernetes Service (LoadBalancer type)** – Exposes the application externally through OCI load balancing
* **NGINX Container Image** – Example web application used for demonstration

---

## Repository Structure

architecture/
Contains architecture diagrams describing the deployment model.

kubernetes-manifests/
Contains Kubernetes YAML files used to deploy and expose the web application.

README.md
Project documentation describing architecture, deployment workflow, and learning outcomes.

---

## Deployment Workflow

A typical deployment workflow for deploying an application on Oracle Kubernetes Engine includes the following steps:

1. Provision an Oracle Kubernetes Engine (OKE) cluster in OCI.
2. Configure kubectl access to communicate with the cluster.
3. Deploy application resources using Kubernetes manifests.
4. Expose the application externally using a Kubernetes Service of type LoadBalancer.
5. Verify that the application is accessible through the load balancer endpoint.

Example commands:

kubectl apply -f kubernetes-manifests/deployment.yaml

kubectl apply -f kubernetes-manifests/service.yaml

Verify application resources:

kubectl get pods

kubectl get svc

Once deployed, the service will provision an OCI load balancer that allows external users to access the application.

---

## Learning Outcomes

Through this project, the following concepts can be understood:

* Deployment of containerized workloads on Oracle Kubernetes Engine
* Integration between Kubernetes services and OCI load balancers
* Basic Kubernetes application deployment using YAML manifests
* Exposure of web applications to external users using Kubernetes networking

---

## Real-World Use Case

Organizations increasingly adopt containerized architectures to improve application scalability and deployment flexibility. Oracle Kubernetes Engine enables teams to deploy microservices and web applications in a managed Kubernetes environment while leveraging OCI's reliable infrastructure.

This architecture can serve as a foundational reference for deploying APIs, microservices, and modern web applications in Oracle Cloud Infrastructure.

---

## Author

Durga Prasad
Oracle ACE Program – Apprentice Stage
