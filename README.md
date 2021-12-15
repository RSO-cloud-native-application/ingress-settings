# Uniborrow ingress settings

This repository contains the configuration files for the Nginx ingress
service that runs on the Google Cloud.

To setup the nginx ingress to run on Kubernetes run:

```bash
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install nginx-ingress ingress-nginx/ingress-nginx
```

The `ingress-resources.yaml` file contains the configuration. The
configuration specifies the rewrite rules. The services are rerouted
based on the first part of the url. The rest of the url is forwarded
to the service (rewrite-target indicates this -> $2 as /sth/$2 ->
/$2).

To apply the changes run:

```bash
kubectl apply -f ingress-resources.yaml
```
