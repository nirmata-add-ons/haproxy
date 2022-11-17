# Haproxy Ingress Controller

[Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) controller
implementation for [HAProxy](http://www.haproxy.org/) loadbalancer.

[![build](https://img.shields.io/github/workflow/status/jcmoraisjr/haproxy-ingress/build?logo=github)](https://github.com/jcmoraisjr/haproxy-ingress/actions/workflows/build.yaml) [![helm](https://img.shields.io/badge/helm%20chart-ready-blue?logo=helm)](https://artifacthub.io/packages/helm/haproxy-ingress/haproxy-ingress)

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

