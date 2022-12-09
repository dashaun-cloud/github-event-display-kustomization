# GitHub Event Display Kustomization

For use with [FluxCD](https://fluxcd.io) to deploy [Knative Eventing github-source](https://github.com/knative/docs/tree/main/code-samples/eventing/github-source)

## Add the GitRepository

```bash
flux create source git github-event-display \
  --url=https://github.com/dashaun-cloud/github-event-display-kustomization \
  --branch=main \
  --export > ./clusters/cluster00/github-event-display-kustomization-source.yaml
```

## Add the Kustomization

```bash
flux create kustomization github-event-display \
  --depends-on knative-eventing \
  --source=github-event-display \
  --path="./kustomize" \
  --prune=true \
  --export > ./clusters/cluster00/github-event-display-kustomization.yaml
```