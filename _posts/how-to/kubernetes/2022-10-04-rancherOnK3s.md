---
title: Install rancher on k3s cluster
date: 2022-10-04
categories: [How-to, Kubernetes]
tags: [kubernetes,k8s,k3s,rancher,howto]     # TAG names should always be lowercase
---

Below are the steps I took too install rancher on k3s cluster. To view up to date information visit offical docs at https://docs.ranchermanager.rancher.io/getting-started/quick-start-guides/deploy-rancher-manager/helm-cli.

Run the below commands

```shell
helm repo add rancher-latest https://releases.rancher.com/server-charts/latest

kubectl create namespace cattle-system

kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.7.1/cert-manager.crds.yaml

helm repo add jetstack https://charts.jetstack.io

helm repo update
```

Below are the commands to install cert-manager and rancher. Be sure to update values in rancher install command before running.
```shell
helm install cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --create-namespace \
  --version v1.7.1

# Windows Powershell
helm install cert-manager jetstack/cert-manager `
  --namespace cert-manager `
  --create-namespace `
  --version v1.7.1


helm install rancher rancher-latest/rancher \
  --namespace cattle-system \
  --set hostname=<IP_OF_LBVS> \
  --set replicas=1 \
  --set bootstrapPassword=<PASSWORD_FOR_RANCHER_ADMIN>

# Windows Powershell
helm install rancher rancher-latest/rancher `
  --namespace cattle-system `
  --set hostname=<IP_OF_LBVS> `
  --set replicas=1 `
  --set bootstrapPassword=<PASSWORD_FOR_RANCHER_ADMIN>
```