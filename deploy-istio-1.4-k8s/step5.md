
Now that the Bookinfo services are up and running, you need to make the application accessible from outside of your Kubernetes cluster, e.g., from a browser. An Istio Gateway is used for this purpose.

1. Define the ingress gateway for the application

`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/bookinfo-gateway.yaml`{{execute}}

2. Confirm the gateway has been created
   `kubectl get gateway`{{execute}}