nested inside one another and each Kubernetes resource can only be in one namespace.

Kubernetes starts with the four initial namespaces:

The default namespace for objects with no other namespace.

The namespace for objects created by the Kubernetes system.

This namespace is created automatically and is readable by all users (including those not authenticated). This namespace is mostly reserved for cluster usage, in case some resources should be visible and readable publicly throughout the whole cluster. The public aspect of this namespace is only a convention, not a requirement.

This namespace for the lease objects associates with each node which improves the performance of the node heartbeats as the cluster scales.