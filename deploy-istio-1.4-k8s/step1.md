To start, launch the Kubernetes cluster. This will launch a two-node Kubernetes cluster with one master and one node.

`launch.sh`{{execute}}

#### Health Check

Once started, you can get the status of the cluster with `kubectl cluster-info`{{execute}}

To be sure you have at least one worker node. If you see only master node in the katacode then restart it. (refresh page)
`kubectl get nodes`{{execute}}

Output:


| NAME        | STATUS           | ROLES  |  AGE | VERSION|
| ------------- |:-------------:| -----:|-----:|-----:|
| master     | Ready | master| 13m| v1.14.0|
| node01      | Ready      |  < none> |13m| v1.14.0|
