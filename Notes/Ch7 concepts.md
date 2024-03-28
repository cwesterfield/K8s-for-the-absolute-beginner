## Services
A Service defines a logical set of Pods and a way to access them

### Section 1 Nodeport
Using service, can expose ports like in docker

#### Service Types
1. Nodeport 
    1. expose port to LAN
    1. NodePort:Port:TargetPort
        1. Node ports have to be 30000-32767
        1. If you don't provide a TargetPort, its assumed to be same as Port. If no NodePort is provided, random port assigned. 
1. ClusterIP
    1. virtual ip inside cluster allowing pods to talk to each other
1. Loadbalancer
    1. LB to allow traffic to be balanced

`kubectl get services` or `kubectl get svc`

`kubectl describe services`

### Section 2 ClusterIP

Creates a VIP between deployments so that other groups of pods have a single place to access.

Ex: A group of 5 nginx servers gets 10.244.1.200 that another deployment can see.

### Section 3 Load Balancer

In supported cloud environments, you can just change the Nodeport Config "spec type" to LoadBalancer and it will automatically work. If its not supported, it will act just like a NodePort.