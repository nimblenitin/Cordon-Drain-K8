# Cordon-Drain-K8
Cordon allows you to retrict any new creation of Pod on a node, while drain allows you to drain a node such that existing pods are moved to a new node. These are useful while doing upgrade of a node.

Simple example-

PS: You need a minimum of two node for this exercise.

*As Root*
```

1. Create a deployment and check on which node it is created
$ kubectl apply -f deployment_one.yaml
$ kubectl get pod -o wide

2. Cordone a node and create another deployment. New Pods will not be created in the node which has been cordoned.
$ kubectl cordon <IP address of node>
$ kubectl apply -f deployment_two.yaml
$ kubectl get pod -o wide

3. Drain a Pod and see that the existing pods are shifted to a new node. Finally, uncordon the node.
$ kubectl drain <IP address of node>
$ kubectl get pod -o wide
$ kubectl uncordon <IP address of node>

```
*As Root*



