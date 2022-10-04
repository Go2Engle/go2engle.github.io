---
title: Setting up HA K3s cluster  
date: 2022-10-04
categories: [How-to, Kubernetes]
tags: [kubernetes,k8s,k3s,howto]     # TAG names should always be lowercase
---

Below are the steps I took too create a HA local db k3s cluster utilizing a LBVS IP.

Have 3 linux nodes ready. In my case Im using 3 ubuntu 20.04 LTS nodes

1. On the first node run:
    ```shell
    sudo curl -sfL https://get.k3s.io | K3S_TOKEN=SECRET sh -s - server --cluster-init --tls-san <LBVS_IP>
    sudo cat /var/lib/rancher/k3s/server/node-token
    ```
2. On the 2nd and 3rd node run:
    ```shell
    sudo curl -sfL https://get.k3s.io | K3S_TOKEN=<TOKEN> sh -s - server --server https://<1st node IP>:6443
    ```
3. Back on the first node you can run the below to get your kubeconfig file:
    ```shell
    sudo cat /etc/rancher/k3s/k3s.yaml
    ```
4. Before using this kubeconfig file edit the `server:` address. Change this to your LBVS IP address