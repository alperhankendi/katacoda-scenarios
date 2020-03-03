
Now that the Bookinfo services are up and running, you need to make the application accessible from outside of your Kubernetes cluster, e.g., from a browser. An Istio Gateway is used for this purpose.

1. Define the ingress gateway for the application

`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/bookinfo-gateway.yaml`{{execute}}

2. Confirm the gateway has been created
   `kubectl get gateway`{{execute}}

3. Determining the ingress IP and ports and set the INGRESS_HOST and INGRESS_PORT variables for accessing the gateway. Return here, when they are set.

`export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].nodePort}')`{{execute}}

`export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].nodePort}')`{{execute}}

`export INGRESS_HOST=$(kubectl get po -l istio=ingressgateway -n istio-system -o jsonpath='{.items[0].status.hostIP}'`{{execute}}

4. Set GATEWAY_URL:
`export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT`{{execute}}


## Confirm the app is accessible from outside the cluster

`curl -s http://${GATEWAY_URL}/productpage | grep -o "<title>.*</title>"`{{execute}}

https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage



## Apply default destination rules
Before you can use Istio to control the Bookinfo version routing, you need to define the available versions, called subsets, in destination rules.

Run the following command to create default destination rules for the Bookinfo services:

`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/destination-rule-all.yaml`{{execute}}

## Verify destination rules

You can display the destination rules with the following command:

`kubectl get destinationrules -o yaml`{{execute}}


 Configuring Request Routing 