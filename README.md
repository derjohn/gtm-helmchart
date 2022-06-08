# gtm-helmchart
A Helm Chart for GTM Server-Side (Google Tag Manager Server-Side) on your own k8s cluster

# Example Usage
An Example to deploy a live container with ingress enabled and cert-manager for let'sencrypt.

```
helm --namespace gtm upgrade --install gtm https://github.com/derjohn/gtm-helmchart/archive/refs/heads/main.tar.gz \
--set env.preview_server_url=https://gtm.example.com \
--set env.run_as_preview_server=false \
--set envFrom.create=true \
--set envFrom.container_config_value=12345666 \
--set ingress.className=nginx \
--set ingress.annotations.cert-manager\\.io/cluster-issuer=letsencrypt \
--set ingress.hosts[0].host=gtm.example.com \
--set ingress.hosts[0].paths[0].path=/ \
--set ingress.hosts[0].paths[0].pathType=ImplementationSpecific \
--set ingress.tls[0].hosts={gtm.example.com} \
--set ingress.tls[0].secretName=ingress-tls-cert-gtm.example.com

```
