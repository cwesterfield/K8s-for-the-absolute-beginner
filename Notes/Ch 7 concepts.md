## Services
A Service defines a logical set of Pods and a way to access them

### Section 1 Nodeport
Using service, can expose ports like in docker

#### Service Types
1. Nodeport 
    1. expose port to LAN
    1. NODE SIDE:POD SIDE
        1. Node ports have to be 30000-32767
1. ClusterIP
1. Loadbalancer