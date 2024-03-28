### Networking
Node is usually on LAN

Pods get internal IPs based on a subnet that is setup inside the node.
In example, its 10.244.0.0

If there are multiple nodes in a single cluster, each node needs a different internal subnet that can allows nodes AND pods to communicate without NAT.

There are many solutions to this, like calico and flannel.