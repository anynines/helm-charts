# Helm web redirect

![Version: 0.0.1-alpha](https://img.shields.io/badge/Version-0.0.1--alpha-informational?style=flat-square)

A Helm chart to create web redirects using an Ingress in Kubernetes

**Homepage:** <https://anynines.github.io/helm-charts>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Maximilian Mueller | <mmueller@anynines.com> | <https://managed-services.anynines.com/> |

## Source Code

* <https://github.com/anynines/helm-charts>

## Requirements
* a Kubernetes cluster with a Nginx Ingress installed (i.e. [ingress-nginx](https://artifacthub.io/packages/helm/ingress-nginx/ingress-nginx))
* [Helm CLI](https://helm.sh/docs/intro/install/)

## Installing the chart
To install the chart:
```shell
$ helm repo add anynines https://anynines.github.io/helm-charts
$ helm install my-redirect anynines/webredirect
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| fullnameOverride | string | `""` | override full name |
| ingress.annotations | object | `{}` | additional annotations for the Ingress Resource |
| ingress.className | string | `"nginx"` | className for the Ingress Controller (only Nginx Controllers are supported) |
| ingress.destination.host | string | `"example.com"` | Hostname of the destination |
| ingress.destination.path | string | `"/"` | Path to redirect to at the destination |
| ingress.destination.port | int | `443` | Port used on the destination |
| ingress.destination.redirect_code | int | `301` | Redirect-Code for the type of redirect, see [redirection_messages](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#redirection_messages) |
| ingress.source.hosts | list | `[]` | URLs that should be redirected to the destination |
| ingress.tls.enabled | bool | `false` | enable/disable TLS certificates (clusterissuer should be configured using annotations) |
| nameOverride | string | `""` | override release name |

## Examples
### simple redirect
```yaml
ingress:
  annotations:
    cert-manager.io/cluster-issuer: letsencrypt-staging
  source:
    hosts:
      - change1.me
      - change2.me
  destination:
    host: "www.anynines.com"
  tls:
    enabled: true
```

### Redirect to subpath
```yaml
ingress:
  annotations:
    cert-manager.io/cluster-issuer: letsencrypt-staging
  source:
    hosts:
      - change3.me
      - change4.me
  destination:
    host: "www.anynines.com"
    path: "/de"
  tls:
    enabled: true
```
