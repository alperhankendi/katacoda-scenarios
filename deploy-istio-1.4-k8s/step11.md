## Trafic Management 

### Fault Injection

Another way to test microservice resiliency is to introduce an HTTP abort fault. In this task, you will introduce an HTTP abort to the ratings microservices for the test user jason.

##### 1. Before you begin

Apply application version routing by either performing the request routing task or by running the following commands

`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/virtual-service-all-v1.yaml`{{execute}}
`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/virtual-service-reviews-test-v2.yaml`{{execute}}

With the above configuration, this is how requests flow:

* productpage → reviews:v2 → ratings (only for user jason)
* productpage → reviews:v1 (for everyone else)

##### 2. Injecting an HTTP abort fault

- Create a fault injection rule to send an HTTP abort for user jason:

`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/virtual-service-ratings-test-abort.yaml`{{execute}}

* Confirm the rule was created:

`kubectl get virtualservice ratings -o yaml`{{execute}}

##### 3. Testing the abort configuration
   
Open https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage  web page, log in as user <b>jason</b> (user:jason,pass:jason) 

If the rule propagated successfully to all pods, the page loads immediately and the Ratings service is currently unavailable message appears.


If you log out from user jason, you will see that /productpage still calls reviews:v1 (which does not call ratings at all) for everybody but jason.
