## Observability 

##### Visualizing your mesh

` KIALI_USERNAME=$(read -p 'Kiali Username: ' uval && echo -n $uval | base64)`{{execute}}

`KIALI_PASSPHRASE=$(read -sp 'Kiali Passphrase: ' pval && echo -n $pval | base64)`{{execute}}

`NAMESPACE=istio-system`{{execute}}
`kubectl create namespace $NAMESPACE`{{execute}}

`cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: Secret
metadata:
  name: kiali
  namespace: $NAMESPACE
  labels:
    app: kiali
type: Opaque
data:
  username: $KIALI_USERNAME
  passphrase: $KIALI_PASSPHRASE
EOF`{{execute}}


`istioctl manifest apply --set values.kiali.enabled=true`{{execute}}

#### Remotely Accessing Kiali Addons

1. Apply networking configuration for the telemetry addons.
`kubectl apply -f assets/kiali.yaml`{{execute}}
2. Visit the Kiali addons via browser.
   https://[[HOST_SUBDOMAIN]]-15029-[[KATACODA_HOST]].environments.katacoda.com/

   *Username: admin*
   *Password: admin* 

#### Let's play with Kiali

1. Make some requests continually with:

`watch -n 1 curl -o /dev/null -s -w %{http_code} $GATEWAY_URL/productpage`{{execute}}

![architecture](assets/kiali-ui-sample.png)
