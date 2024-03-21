### Architechture 
Nodes (once called minions) are where k8s is installed

Master is the node in charge
and does the orchestration

k8s install is 

 - api server
 - etcd
 - kubelet
 - container runtime
 - controller
 - scheduler

 Master has
 - api server
 - etcd
 - container runtime
 - controller
 - scheduler

Nodes have
 - kubelet

### Common commands
```
kubectl run
kubectl cluster-info
kubectl get nodes
kubectl delete
```