# Kubernetes Manifests for React UI

This repository contains Kubernetes manifests for deploying a React UI application, including Service, Deployment, and Horizontal Pod Autoscaler (HPA) resources.

## Files
- `main.yaml`: Contains all the Kubernetes resources required for the React UI application.

## Resources

### 1. Service
- **Type:** NodePort
- **Name:** ui-service
- **Ports:**
  - 8080 (http)
- **Labels:**
  - app: react-ui
  - env: prod

### 2. Deployment
- **Name:** react-ui
- **Replicas:** 4
- **Image:** pavank95/ui
- **Resources:**
  - Requests: 1 CPU, 2Gi memory
  - Limits: 1 CPU, 2Gi memory
- **Labels:**
  - app: react-ui
  - env: prod

### 3. Horizontal Pod Autoscaler (HPA)
- **Min Replicas:** 4
- **Max Replicas:** 10
- **Target CPU Utilization:** 50%
- **Scale Target:** react-ui Deployment

## Usage
Apply all resources with:

```sh
kubectl apply -f main.yaml
```

## Customization
- Edit `main.yaml` to change replica counts, resource requests/limits, image, or environment labels as needed.
- Update the HPA section to adjust autoscaling behavior.

## Prerequisites
- Kubernetes cluster
- kubectl configured to access your cluster

---
For Helm-based deployments or environment-specific overrides, see the `charts/` directory if present.
