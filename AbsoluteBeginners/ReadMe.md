# Core concepts

## Kubernetes Architecture


1. Node: its a machine, Physical or virtual in which K8 is installed .<br>
but what if the node dies, what will happen to the application thats installed inside the node?

2. Cluster: Cluster is a set of nodes grouped together . <br>
    This way, if one node fails then your application is still accessible through other nodes.
    Now we got cluster, but who is responsible for managing the cluster? Where is the information of the member of the cluster stored?

3. Master Node: Master also sits inside the cluseter. <br>
It manages the Worker nodes and if one fails then it tries to make the other node get the job done .

4. API Server: This acts like the frontend for the Kubernetes services .
5. etcd: it stores all the data managed by the cluster in the key value pair .
6. Scheduler: it is responsible for distributing work or containers across multiple nodes .<br>
    it looks for newly created containers and assigns them to nodes .
7. Controller: They are the brain behind the orchestration . They are responsible for noticing when nodes or endpoints goes down .<br>
Controllers make decisions to bring up new containers in such scenarios .

8. Container Runtime: its the underlying software that is used to run the container.<br>
In this scenario its the docker .

9. Kubelet: Its the agent that runs on each node of the cluster .<br>
Agents make sure that the containers are running at nodes as expected .

**How does one server becomes master and the other as the worker node?** <br>
worker node is where the containers are hosted ; for example docker container.<br>
To run docker container in a system we need container runtime installed .

The master server has the **kubeAPI server** that makes it the master.

similarly, worker node has the **Kubelet** installed which is responsible for interacting <br>
with master to provide health information about the worker node and carry out action requested<br>
by the master in the worker nodes.

All the information that Kubelet provides to the master are stored in the key value **(etcd)** in the master.

The master also has the **controller manager** and the **scheduler.**

**kubectl:** <br>
Its the command line utility used in Kubernetes. <br>
its used to deploy and manage applications on a Kubernetes Cluster .

```
kubectl run hellow-minikube
```

The above mentioned command is used to deploy an application on the cluster .

```
λ kubectl cluster-info
Kubernetes control plane is running at https://kubernetes.docker.internal:6443
CoreDNS is running at https://kubernetes.docker.internal:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```
its used to display the cluster information .

```
λ kubectl get nodes
NAME             STATUS   ROLES                  AGE   VERSION
docker-desktop   Ready    control-plane,master   25h   v1.22.5
```
it is used to display the nodes available in the cluster .



## Pods

Pods comes into the picture after the application has been deployed to docker hub .<br>
We also assume that the Kubernetes cluster has also been set up and is working .

> Kubernetes does not deploy containers directly on the worker node .

The containers are encapsulated in to a Kubernetes object as pods .<br>
A pod is a single instance of an application .<br>
A pod is a smallest object that we can create in Kuberenetes .<br>

One Node can accomodate multiple pods .

> Basically , Pods usually have a one to one relationship with containers running in your applications .

A pod can have multiple containers running inside it; provided the are not of the same kind .<br>
You can not run two python containers inside one pod.<br>
you can run one python container and one sql container in one pod .<br>
The two containers inside the pod can communicate with each other as they share the same local host .

**Now lets see how to deploy to pods**<br>

```kubectl

kubectl run nginx

```

when we run this command, it creates a pod and deploys the nginx image inside the pod .<br>
But where does it know where to get the image from ?<br>
for that we need to append the above command with **--image nginx**<br>
so now the commands becomes

```
kubectl run nginx --image nginx
```

## Pods with YAML

in this section,we will create a pod using a YAML based configuration .

Kubernetes uses YAML files as inputs for creation of the objects such as <br>
pods, replicas, deployments, services etc 




















