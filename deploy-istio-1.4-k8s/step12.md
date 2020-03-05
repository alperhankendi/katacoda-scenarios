## Trafic Management 

### Traffic Shifting

A common use case is to migrate traffic gradually from one version of a microservice to another. In Istio, you accomplish this goal by configuring a sequence of rules that route a percentage of traffic to one service or another. 

In this section,we will send 50% of traffic to reviews:v1 and 50% to reviews:v3. Then, you will complete the migration by sending 100% of traffic to reviews:v3.


##### Apply weight-based routing

1. To get started, run this command to route all traffic to the v1 version of each microservice.

`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/virtual-service-all-v1.yaml`{{execute}}

2. Open https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage  web page 

    Notice that the reviews part of the page displays with no rating stars, no matter how many times you refresh. This is because you configured Istio to route all traffic for the reviews service to the version reviews:v1 and this version of the service does not access the star ratings service.

3. Transfer 50% of the traffic from reviews:v1 to reviews:v3

`clear;cat istio-1.4.6/samples/bookinfo/networking/virtual-service-reviews-50-v3.yaml`{{execute}}

 4. Apply changes with the following command:

`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/virtual-service-reviews-50-v3.yaml`{{execute}}

5. Refresh the /productpage in your browser and you now see red colored star ratings approximately 50% of the time. This is because the v3 version of reviews accesses the star ratings service, but the v1 version does not.
----

For for information about version routing with autoscaling, check out the blog article [Canary Deployments using Istio.](https://istio.io/blog/2017/0.1-canary/)

---

##### Cleanup 

Remove the application routing rules:

`kubectl delete -f samples/bookinfo/networking/virtual-service-all-v1.yaml`{{execute}}


