# Everything Wrong with GKE

_nuances, missing features, strange API, things to watchout, and wishlist_

## Severe System Overhead

GKE severely over-provisions cpu and memory for system.

- GKE does not allow to set cpu requests for `metrics-server` and keeps resetting it to 300m
- GKE nodes have less memory than hardware node support (4 GB node has 3 GB availble to K8S) [^1]

[^1]: https://docs.cloud.google.com/kubernetes-engine/docs/concepts/plan-node-sizes
