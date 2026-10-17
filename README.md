# Everything Wrong with GKE

_nuances, missing features, strange API, things to watchout, and wishlist_

## Severe System Overhead

GKE severely over-provisions cpu and memory for system.

- GKE does not allow to set cpu for `metrics-server` and keeps resetting it to 300m
- GKE does not allow to set cpu for `kube-dns` and keps resetting it to 270m 
- GKE does not allow to set cpu for `anetd` and keeps restting it to 200m / node
- GKE does not allow to set cpu for `gke-metadata-server` and keeps restting it to 100m / node
- GKE does not allow to set cpu for `fluentbit` and keeps restting it to 100m / node
- GKE does not allow to set cpu for CSI and keeps restting it to 120m / node
- GKE nodes have less memory than hardware node support (4 GB node has 3 GB availble to K8S) [^1]

Your effective memory and CPU is reduced (1GB is taken away immediately), out of remaning 0.5 CPU / node is burning all the time for idle empty node.

If you have `e2-standard-2` you have only 0.5 CPU (**25%**) and 4GB (**50%**) left for any useful workload, you paying for **75%** of CPU and **50%** of memory for "system".

If you have `e2-standard-4` you have only 2.5 CPU (**65%**) and 11GB (**86%**) left for any useful workload, you paying for **35%** of CPU and **14%** of memory for "system".

[^1]: https://docs.cloud.google.com/kubernetes-engine/docs/concepts/plan-node-sizes
