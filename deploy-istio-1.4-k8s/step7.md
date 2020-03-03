## Configuring Request Routing 

### Route based on user identity

now we will change the route configuration so that all traffic from a specific user is routed to a specific service version. In this case, all traffic from a user named <B>Jason</b> will be routed to the service reviews:v2.

*Remember, reviews:v2 is the version that includes the star ratings feature.*
- user:jason
- password:jason

1. Run the following command to enable user-based routing:
   `kubectl apply -f istio-1.4.6/samples/bookinfo/networking/virtual-service-reviews-test-v2.yaml`{{execute}}
2. Confirm the rule is created:
   `kubectl get virtualservice reviews -o yaml`{{execute}}
3. Go to https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage of the Bookinfo app, log in as user jason.   
4. Refresh the browser. The star ratings appear next to each review.
   


You have successfully configured Istio to route traffic based on user identity.

## Clean up your mess
 `kubectl delete -f istio-1.4.6/samples/bookinfo/networking/virtual-service-reviews-test-v2.yaml`{{execute}}
