# Project Overview

This project demonstrates the deployment of a Kubernetes-based application using Argo CD for GitOps and a canary deployment strategy for progressive delivery. It includes the following components:

---

## Components

### 1. **Argo CD**
![Argo CD Logo](https://argo-cd.readthedocs.io/en/stable/assets/argo-cd-logo.png)
Argo CD manages and deploys Kubernetes resources declaratively, ensuring the desired state defined in Git is reflected in the cluster.

### 2. **Canary Deployment**
![Canary Deployment](https://upload.wikimedia.org/wikipedia/commons/3/3a/Canary_deployment_diagram.png)
The canary deployment strategy gradually rolls out changes to a subset of users before a full deployment, minimizing risks.

### 3. **Kubernetes Resources**
- **Ingress**: Manages external access to the services.
- **Services**: Provides stable networking endpoints for the application.
- **Rollouts**: Manages the canary deployment process.

---

## Folder Structure

```plaintext
apps/
  canary-demo/
    canary-demo-ingress.yaml
    canary-demo-lb-service.yaml
    rollout.yaml
    service.yaml
argocd/
  app.yaml
```

### `apps/canary-demo`
Contains the Kubernetes manifests for the canary-demo application:
- `canary-demo-ingress.yaml`: Defines the ingress resource for external access.
- `canary-demo-lb-service.yaml`: Defines the load balancer service.
- `rollout.yaml`: Manages the canary deployment strategy.
- `service.yaml`: Defines the cluster-internal service.

### `argocd`
Contains the Argo CD application manifest:
- `app.yaml`: Defines the Argo CD application resource to manage the `canary-demo` application.

---

## How It Works

1. **Argo CD Setup**:
   - Install Argo CD in the Kubernetes cluster.
   - Apply the `app.yaml` file in the `argocd` folder to create an Argo CD application.

2. **Canary Deployment**:
   - The `rollout.yaml` file defines the canary deployment strategy.
   - Changes are rolled out gradually, and metrics are monitored to ensure stability.

3. **Ingress and Services**:
   - The `canary-demo-ingress.yaml` file exposes the application externally.
   - The `service.yaml` and `canary-demo-lb-service.yaml` files define networking within the cluster.

---

## Use Case

This project is ideal for:
- Demonstrating GitOps workflows with Argo CD.
- Implementing progressive delivery using canary deployments.
- Managing Kubernetes resources declaratively.

---

## Getting Started

1. **Install Argo CD**:
   - Follow the [official documentation](https://argo-cd.readthedocs.io/en/stable/) to install Argo CD in your cluster.

2. **Apply the Manifests**:
   - Deploy the Argo CD application:
     ```bash
     kubectl apply -f argocd/app.yaml
     ```
   - Deploy the canary-demo application:
     ```bash
     kubectl apply -f apps/canary-demo/
     ```

3. **Access the Application**:
   - Use the ingress URL defined in `canary-demo-ingress.yaml` to access the application.

4. **Monitor the Deployment**:
   - Use Argo CD's dashboard to monitor the application state.
   - Observe the canary rollout process and verify metrics.

---

## Conclusion

This project showcases GitOps and progressive delivery in Kubernetes, combining Argo CD and canary deployments for safe and reliable updates.