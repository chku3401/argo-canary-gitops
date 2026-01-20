# GitOps Repository

This repository contains the GitOps structure for managing Kubernetes resources with Argo CD and Argo Rollouts.

## Structure

- `applications/`: Contains Argo CD application manifests.
- `environments/`: Contains environment-specific configurations (e.g., dev, staging, production).
- `services/`: Contains Kubernetes manifests for individual services.

## Usage

1. Clone this repository.
2. Apply the manifests using `kubectl` or Argo CD.
3. Monitor deployments and rollouts using the Argo CD and Argo Rollouts dashboards.