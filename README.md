# mitmproxy-kube

Kubectl/Kustomize configs for deploying [mitmproxy][] to Kubernetes.

## What's in the box?

- `config/proxy/`: base YAML manifests for [mitmproxy][] `Namespace`,
  `Deployment` and `Service`, exposing port 8080 as proxy-port
- `config/default/`: default customization, produces the base manifests from
  `config/proxy/` with additional common labels
- `config/dump/`: everything in `config/default/` + the proxy command set to
  `mitmdump` to run in headless mode
- `config/web/`: everything in `config/default/` + [mitmproxy][] web interface
  on port 8081

## How do I use this?

``` sh
# To deploy the base config (which does nothing)
kubectl apply -k config/default/

# To deploy the dump config (which runs in headless mode printing connections
# and flows to stdout)
kubectl apply -k config/dump/

# To deploy the web config (which runs the proxy and the web interface)
kubectl apply -k config/web/
```

[mitmproxy]: https://mitmproxy.org/
