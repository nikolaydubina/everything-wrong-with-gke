# Everything Wrong with GKE

_nuances, missing features, strange API, things to watchout, and wishlist_

## Severe System Overhead

- GKE does not allow to set cpu requests for `metrics-server` and keeps resetting it to 300m
