### Microservices Architechture

Sample application stack , 5 deployments or pods

#### Docker

Create Redis container

Create Postgres

Create voting-app and expose 5000 to internal port 80

Create result-app and expose 5001 to internal port 80

Create worker app

Use Docker links (docker run --links) to allow container to talk to each other

ex: docker run -d --name vote -p 5000:80 --links redis:redis voting-app


#### K8s

Goal: Deploy 5 pods, enable conectitivity, enable external access

1. Deploy Pods
1. Create Services (ClusterIP (node to node access))
    1. redis
    1. db
1. Create Services (NodePort (Because they are externally accessed))
    1. voting-app
    1. results-app


Service is ONLY required when something needs to be exposed outside the pod

`kubectl get pods,svc` will get boths pods and services!