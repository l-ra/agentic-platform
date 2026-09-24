# agenticka-platforma

Samostatná statická aplikace. `index.html` je zdroj aplikace; Helm chart v
tomto adresáři ho při nasazení vloží do ConfigMap a připojí do nginx podu.
Není potřeba vlastní image registry.

## Kontrola

```sh
helm lint .
helm template agenticka-platforma . --namespace agenticka-platforma
```

## Nasazení

```sh
../deploy.sh ./agenticka-platforma
```

Výchozí nastavení používá kubeconfig `/home/rasekl/.kube/config-oc`, namespace
`agenticka-platforma`, Traefik ingress a cert-manager ClusterIssuer
`letsencrypt-prod`.
