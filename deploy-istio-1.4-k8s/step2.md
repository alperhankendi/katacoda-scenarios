Istio is installed in two parts. The first part involves the CLI tooling that will be used to deploy and manage Istio backed services. The second part configures the Kubernetes cluster to support Istio.

## Install CLI tooling

The following command will install the Istio 1.4.6 release.

`curl -L https://istio.io/downloadIstio | sh -`{{execute}}

After it has successfully run, add the bin folder to your path.

`export PATH="$PATH:/root/istio-1.4.6/bin"`{{execute}}

## Verify Istio

Begin the Istio pre-installation verification check by running:
`istioctl verify-install`{{execute}}

You should see the message like;

Install Pre-Check passed! The cluster is ready for Istio installation.

## Install Istio

These instructions assume you are new to Istio, providing streamlined instruction to install Istio’s built-in demo configuration profile. This installation lets you quickly get started evaluating Istio.

`istioctl manifest apply --set profile=demo`{{execute}}

You can find more installation config profile option [here](https://istio.io/docs/setup/additional-setup/config-profiles/)

<b>The Demo Profile is not recomended for production.This profile enables high levels of tracing and access logging so it is not suitable for performance tests</b>
## Check Status

Verify the installation by ensuring the following Kubernetes services are deployed.

`kubectl get svc -n istio-system`{{execute}}

Also ensure corresponding Kubernetes pods are deployed and have a STATUS of Running:

`kubectl get pods -n istio-system`{{execute}}