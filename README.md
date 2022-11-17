# Haproxy Ingress Controller

[Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) controller
implementation for [HAProxy](http://www.haproxy.org/) loadbalancer.


HAProxy Ingress is a Kubernetes ingress controller: it configures a HAProxy instance
to route incoming requests from an external network to the in-cluster applications.
The routing configurations are built reading specs from the Kubernetes cluster.
Updates made to the cluster are applied on the fly to the HAProxy instance.

## Use HAProxy Ingress

**Documentation:**

* Getting started guide: [/docs/getting-started/](https://haproxy-ingress.github.io/docs/getting-started/)
* Global and per ingress/service configuration keys: [/docs/configuration/keys/](https://haproxy-ingress.github.io/docs/configuration/keys/)
* Command-line options: [/docs/configuration/command-line/](https://haproxy-ingress.github.io/docs/configuration/command-line/)

**Supported versions:**

| HAProxy Ingress   | Supported<br/>Kubernetes | 
|-------------------|--------------------------|
| [`v0.13.6`]       |       `1.19+`            |                 

**Steps to delete haproxy:**
#kubeconfig file location of cluster
kubeconfig=$1
#name value is haproxy
name=$2
# namspace is ingress-haproxy
namespace=$3
kubectl --kubeconfig=$kubeconfig  get crd | grep -i $2 | awk {'print $1'} | xargs kubectl --kubeconfig=$kubeconfig delete crd
sleep 2
kubectl --kubeconfig=$kubeconfig  get clusterrole | grep -i $2 | awk {'print $1'} | xargs kubectl --kubeconfig=$kubeconfig delete clusterrole
sleep 2
kubectl --kubeconfig=$kubeconfig get clusterrolebinding | grep -i $2 |  awk {'print $1'} | xargs kubectl --kubeconfig=$kubeconfig delete clusterrolebinding
sleep 2
kubectl --kubeconfig=$kubeconfig get mutatingwebhookconfigurations | grep -i $2 |  awk {'print $1'} | xargs kubectl --kubeconfig=$kubeconfig delete mutatingwebhookconfigurations
sleep 2
kubectl --kubeconfig=$kubeconfig get validatingwebhookconfigurations | grep -i $2 |  awk {'print $1'} | xargs kubectl --kubeconfig=$kubeconfig delete validatingwebhookconfigurations
sleep 2
kubectl --kubeconfig=$kubeconfig get sa -n $namespace | grep -i $2 | awk {'print $1'} | xargs kubectl --kubeconfig=$kubeconfig -n $namespace delete sa
sleep 2
kubectl --kubeconfig=$kubeconfig get role -n $namespace | grep -i $2 | awk {'print $1'} | xargs kubectl --kubeconfig=$kubeconfig -n $namespace delete role 
kubectl --kubeconfig=$kubeconfig get rolebinding -n $namespace | grep -i $2 | awk {'print $1'} | xargs kubectl --kubeconfig=$kubeconfig -n $namespace delete rolebinding
kubectl --kubeconfig=$kubeconfig get cm -n $namespace | grep -i $2 | awk {'print $1'} | xargs kubectl --kubeconfig=$kubeconfig -n $namespace delete cm 
