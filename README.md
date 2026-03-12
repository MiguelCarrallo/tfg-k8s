# Kubernetes Enterprise Environment – Final Degree Project
> Design and implementation of a secure, observable and scalable Kubernetes infrastructure using Minikube and AWS EKS.

This repository contains the implementation of a Kubernetes-based enterprise environment developed as part of a Final Degree Project.

The objective of this project was to design and deploy a **secure, observable, and scalable Kubernetes infrastructure**, applying real-world DevOps and cloud architecture principles.

The environment was initially implemented in a **local Kubernetes cluster using Minikube** and later adapted to run in **AWS EKS**.

---

## Architecture Overview

The Kubernetes environment includes several key infrastructure components typically present in enterprise deployments:

- Namespace segmentation
- Role-Based Access Control (RBAC)
- Network Policies for traffic isolation
- Persistent storage using PV and PVC
- ResourceQuota configuration
- Observability stack (Prometheus + Grafana)
- Ingress configuration for external access
- AWS IAM policy integration

These components allow the cluster to simulate a **production-like environment with security, monitoring, and resource management.**

---

## Repository Structure

```
aws/
└── iam_policy.json
    IAM configuration used for AWS integration.

manifests/
├── namespaces.yaml
├── quota-dev.yaml
├── netpol-deny-ingress.yaml
├── netpol-allow-monitoring.yaml
│
├── apps/
│   Example Kubernetes workloads deployed in the cluster.
│
├── ingress/
│   Resources used to expose services externally.
│
├── network/
│   Additional networking configurations.
│
├── observabilidad/
│   Monitoring stack configuration including Prometheus and Grafana.
│
├── rbac/
│   Role-Based Access Control configuration.
│
└── storage/
    PersistentVolume and PersistentVolumeClaim configuration.
```

---

## Kubernetes Components Implemented

### Namespace Segmentation

Different namespaces were used to logically isolate environments and services inside the cluster.

Example environments:

- `dev`
- `pre`
- `monitoring`

This allows better resource management and access control.

---

### RBAC (Role-Based Access Control)

RBAC policies were implemented to control access to cluster resources.

Different user profiles were defined to simulate real-world scenarios such as:

- administrator access
- development access
- read-only environments

---

### Network Policies

NetworkPolicies were applied to restrict pod-to-pod communication and enforce security boundaries inside the cluster.

Example policies include:

- default deny ingress policy
- allow traffic only from monitoring namespace

This ensures that only authorized components can communicate with specific workloads.

---

### Persistent Storage

Persistent storage was implemented using:

- PersistentVolumes (PV)
- PersistentVolumeClaims (PVC)

This allows workloads to store data independently from the pod lifecycle.

---

### Observability Stack

Monitoring capabilities were implemented using:

- **Prometheus** for metrics collection
- **Grafana** for visualization

This stack allows monitoring cluster performance, resource usage, and application metrics.

---

### Ingress Configuration

Ingress resources were configured to expose services externally and simulate real application access patterns.

This layer can be integrated with cloud load balancers in AWS environments.

---

## Technologies Used

- Kubernetes
- Minikube
- AWS EKS
- Docker
- Helm
- Prometheus
- Grafana
- YAML infrastructure definitions

---

## Example Deployment

Example of deploying the Kubernetes manifests:

```bash
kubectl apply -f manifests/namespaces.yaml
kubectl apply -f manifests/rbac/
kubectl apply -f manifests/network/
kubectl apply -f manifests/storage/
kubectl apply -f manifests/apps/
```

These commands deploy the main infrastructure components and workloads into the cluster.

---

## Learning Outcomes

Through this project the following concepts were implemented and validated:

- Kubernetes cluster architecture
- Infrastructure as Code using YAML manifests
- Access control with RBAC
- Network security with NetworkPolicies
- Persistent storage management
- Observability implementation
- Migration from local environment to cloud infrastructure

---

## Security Notice

This repository does not include any real credentials or secrets.  
Sensitive configuration values are intentionally omitted or replaced with placeholders.

---

## Author

**Miguel Carrallo Escudero**
