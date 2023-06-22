# anynines Helm Charts

This repository includes Helm Charts managed by [anynines GmbH](https://www.anynines.com).

This repository can be added using the following command:

```
helm repo add anynines https://anynines.github.io/helm-charts
```

# Example of installing a web redirect:
First, create a `values.yaml` (see [Examples](charts/webredirect/README.md#Examples))
```shell
helm repo add anynines https://anynines.github.io/helm-charts
helm install testredirect anynines/webredirect -f values.yaml
```


