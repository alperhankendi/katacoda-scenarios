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


`istioctl manifest apply --set values.kiali.enabled=true` {{execute}}

#### Generating a service graph

1. let's send requests continually with:

`watch -n 1 curl -o /dev/null -s -w %{http_code} $GATEWAY_URL/productpage`{{execute}}

2. To open the Kiali UI, execute the following command in your Kubernetes environment:
   
`istioctl dashboard kiali`{{execute}}
