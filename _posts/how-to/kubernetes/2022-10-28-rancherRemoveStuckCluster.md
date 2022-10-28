---
title: Remove cluster from rancher that is in updating state
date: 2022-10-28
categories: [How-to, Kubernetes]
tags: [kubernetes,k8s,k3s,rancher,howto]     # TAG names should always be lowercase
---

Sometimes when deleting a cluster from rancher it will get in an updating state and will hang. You can force remove this by editing the clusters yaml from cluster managment and set the finalizers to []

```yaml
finalizers: []
```

If you need to run this via the cli use either of the 2 commands below

### RKE1
```shell
kubectl edit clusters.rancher.cattle.io/<cluster_name>
```

### RKE2
```shell
kubectl edit clusters.management.cattle.io/<cluster_name>
```