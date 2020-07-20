# upload ssl certificate to istio ingress gateway for https

## create for the first time, for example use Sectigo ssl
```
kubectl create -n istio-system secret tls istio-ingressgateway-certs \
  --key folder-ssl/star_ssl.key \
  --cert folder-ssl/star_ssl.crt
```

## check key ssl alredy in pod ingressgateway

```
kubectl exec -it -n istio-system \
  $(kubectl -n istio-system get pods \
    -l istio=ingressgateway \
    -o jsonpath='{.items[0].metadata.name}') \
  -- ls -l /etc/istio/ingressgateway-certs/
```
```
total 0
lrwxrwxrwx 1 root root 14 Feb 20 08:39 tls.crt -> ..data/tls.crt
lrwxrwxrwx 1 root root 14 Feb 20 08:39 tls.key -> ..data/tls.key
```
