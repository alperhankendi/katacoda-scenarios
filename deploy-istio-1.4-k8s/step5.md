
Now that the Bookinfo services are up and running, you need to make the application accessible from outside of your Kubernetes cluster, e.g., from a browser. An Istio Gateway is used for this purpose.

1. Define the ingress gateway for the application

`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/bookinfo-gateway.yaml`{{execute}}

2. Confirm the gateway has been created
   `kubectl get gateway`{{execute}}

3. getting ip port

`export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].nodePort}')`{{execute}}

`export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].nodePort}')`{{execute}}

https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage

[[HOST_SUBDOMAIN]]
[[KATACODA_HOST]]

`export INGRESS_HOST=127.0.0.1`{{execute}}
