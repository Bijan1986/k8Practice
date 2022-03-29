# Chapter 2: Kuberenetes Architecture - From running docker Images to Running Pods

## Understanding the difference between the master and the worker nodes :
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


first of all we need to know what are called as nodes in Kuberenetes.

To run Kuberenetes, we need to a Linux machine and these Linux machine are called as nodes .

A Node could be a physical machine or a virtual machine on a cloud provider .

There are two types of nodes in Kubernetes 

1. Master node
2. Worker node

**Master Nodes:** They are responsible for maintaining the state of the Kubernetes Cluster

**Worker Nodes:** Ther take your container and run it inside .

> if you have a windows based node, then you can run the windows based containers.
<br>And if you have a linux based node then you can run a linux based container.
<br>But you can not run a windows container inside a linux node.














