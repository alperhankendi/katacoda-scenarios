
## Install Services
The default Istio installation uses automatic sidecar injection. Label the namespace that will host the application with istio-injection=enabled

`kubectl label namespace default istio-injection=enabled`{{execute}}


Deploy your application using the kubectl command:

`kubectl apply -f istio-1.4.6/samples/bookinfo/platform/kube/bookinfo.yaml`{{execute}}


>If you disabled automatic sidecar injection during installation and rely on manual sidecar injection, use the istioctl kube-inject command to modify the bookinfo.yaml file before deploying your application.
`kubectl apply -f <(istioctl kube-inject -f samples/bookinfo/platform/kube/bookinfo.yaml)`{{execute}}


## Verify Services

Confirm all services and pods are correctly defined and running

`kubectl get services`{{execute}}

and

`kubectl get po`{{execute}}

To confirm that the Bookinfo application is running, send a request to it by a curl command from some pod, for example from ratings:

`kubectl exec -it $(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}') -c ratings -- curl productpage:9080/productpage | grep -o "<title>.*</title>"`{{execute}}