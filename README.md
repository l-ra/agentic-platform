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

## GitHub Pages

Statická prezentace (`index.html`) a složka `docs/` se dají publikovat jako
GitHub Pages bez vlastního buildu.

### Jednorázové nastavení v repozitáři

1. **Settings → Pages**
2. **Build and deployment → Source:** GitHub Actions
3. Po pushi do větve `main` (nebo ručním spuštění workflow **GitHub Pages**)
   se stránka nasadí automaticky.

Adresa bude ve tvaru `https://<owner>.github.io/agentic-platform/`.

Soubor `.nojekyll` v repozitáři vypíná zpracování Jekyll — bez něj by Helm
šablony s `{{ … }}` mohly rozbít build.
