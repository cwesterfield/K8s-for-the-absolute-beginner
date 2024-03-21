## Pods with yaml Lab

`kubectl get pods`

get short list of running pods with container count, status, restarts, and age

`kubectl describe pod $PODNAME`

Get details of pod, including image used, mounts, and errors

`kubectl get pods -o wide`

Get pod info with extra detail like what node pods are in

`kubectl run redis --image=redis`

Create a pod running redis

`kubectl run redis --image=redis --dry-run=client -o yaml > redis.yaml`

Create a yaml file for pod use 

`kubectl create -f redis.yaml` to build

`kubectl apply -f redis.yaml` if you make changes to yaml file

## Section 6 Replication Controller

Replication controller takes care of makeing sure required count of working nodes are operating

New Kid on the Block? **Replica Set**

`kubectl get replicationcontroller`

see the controllers and status

`kubectl get replicaset`

Like above, but shows replicasets

Replica Sets can create and or monitor pods 
we define template and match the labels so that if a pod dies, replica set knows how to get back to replicas goal.

If you want to scale (change count of replicas)
```
kubectl replace -f replicaset-def.yaml

kubectl scale --replicas=6 -f replicaset-def.yaml

kubectl scale --replicas=6 replicaset myapp-replicaset
```
Note: using the filename does not update the file (there will be 6 pods, but the file will say 3)

Replica set is able to terminate pods to make sure replicas count is exact (no more, no less)

`kubectl explain replicaset`

Explains kube concepts in the cli

To delete replica sets `kubectl delete rs $RSNAME`

## Section 9 Deployments

**Rolling updates **

  > Don't update all pods at once

**Deployment**

A kind of k8s that allows rollbacks, scale changes and pause and resume of changes

`kubectl get all`

## Section 12 Roullout and versioning

`kubectl rollout status deployment/myapp-deployment`

`kubectl rollout history deployment/myapp-deployment`

Deployment Strategy
1. Recreate strat "Delete all and rebuild"
1. Rolling update (create new updated pd, take one pod down, repeat until done)

Best method for update

Modifiy yaml and then use `kubectl apply -f $FILE.yaml`

Undo

`kubectl rollout undo deployment/myapp-deployment`

Record change reason when creating deployment (will show in rollout history
)

`kubectl create --filename=deployment.yaml --record=true`