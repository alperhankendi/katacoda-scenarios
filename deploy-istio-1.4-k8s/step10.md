## Trafic Management 

### Fault Injection

You will see how to inject faults to test the resiliency of your application.

##### 1. Before you begin

Apply application version routing by either performing the request routing task or by running the following commands

`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/virtual-service-all-v1.yaml`{{execute}}

`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/virtual-service-reviews-test-v2.yaml`{{execute}}

With the above configuration, this is how requests flow:

* productpage → reviews:v2 → ratings (only for user jason)
* productpage → reviews:v1 (for everyone else)

##### 2. Injecting an HTTP delay fault

- Create a fault injection rule to delay traffic coming from the test user jason.

`kubectl apply -f istio-1.4.6/samples/bookinfo/networking/virtual-service-ratings-test-delay.yaml`{{execute}}

* Confirm the rule was created:

`kubectl get virtualservice ratings -o yaml`{{execute}}

##### 3. Testing the delay configuration
   
Open https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage  web page, log in as user <b>jason</b> (user:jason,pass:jason) 

You expect the Bookinfo home page to load without errors in approximately 7 seconds. However, there is a problem: the Reviews section displays an error message:

      Error fetching product reviews!
      Sorry, product reviews are currently unavailable for this book.

View the web page response times:

Open the Developer Tools menu in you web browser.
Open the Network tab
Reload the /productpage web page. You will see that the page actually loads in about 6 seconds.