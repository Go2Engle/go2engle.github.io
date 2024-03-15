---
title: Kubeconfig merging on Windows with Powershell 
date: 2024-04-15
categories: [How-to, Kubernetes, Powershell]
tags: [kubernetes,k8s,k3s,howto,Powershell]     # TAG names should always be lowercase
---

# Merging kubeconfig Files in Windows Using PowerShell

Managing Kubernetes configurations can be a crucial aspect of working efficiently with Kubernetes clusters. In this guide, we will walk through the process of merging a new kubeconfig file into the main kubeconfig file on Windows using PowerShell.

Feel free to customize the instructions below to suit your specific environment and preferences. Following these steps will enable you to efficiently manage kubeconfig files on Windows using PowerShell.

Happy Kubernetizing! 🚀🔧

## Prerequisites

Before proceeding, ensure you have the following:

- PowerShell installed on your Windows machine.
- kubectl command-line tool installed and configured.
- Access to the kubeconfig files you wish to merge.

## Procedure

Replace `<username>` and `<new-config>` with your username and new config file you want to merge.
```powershell
# make a backup
cd ~/.kube/
cp config config.bak

# merge both kube config files
$ENV:KUBECONFIG = "C:\Users\<username>\.kube\config;C:\Users\<username>\.kube\<new-config>"

# verify that the variable is set
$ENV:KUBECONFIG

# output to temp file
kubectl config view --flatten > config-merged

# verify that config-merged is correct
kubectl --kubeconfig=config-merged config get-clusters

# delete backup
rm config

# move merged file to config
mv config-merged config

# remove (optional)
rm config.bak
```

## Managing Contexts

### List All Clusters

To list all clusters configured in your kubeconfig file, use the following command:

```powershell
kubectl config get-clusters
```


### Deleting a Cluster by Name

To delete a cluster from your kubeconfig file by its name, execute the following command:

Replace `<cluster_name>` with the name of the cluster you wish to delete.
```powershell
kubectl config delete-cluster <cluster_name>
```