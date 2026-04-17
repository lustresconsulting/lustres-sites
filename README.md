# lustres-sites

Static marketing sites for Lustres, deployed to the Orbit k3s cluster via ArgoCD.

## Sites

| Site | URL | Directory |
|------|-----|-----------|
| Landing | `lustres.dev` / `www.lustres.dev` | `sites/landing/` |
| Cloud | `cloud.lustres.dev` / `orbit.lustres.dev` | `sites/cloud/` |
| Agentic | `agentics.lustres.dev` | `sites/agentic/` |

## How It Works

Each site is a static HTML directory baked into an `nginx:alpine` Docker image.

1. Push changes to any `sites/*/` directory
2. CI detects which sites changed and builds only those
3. Images are pushed to GHCR as `ghcr.io/lustresconsulting/lustres-{site}:<sha>`
4. CI bot commits the new image tag to the orbit repo values files
5. ArgoCD picks up the change and deploys

## Local Development

To preview a site locally:

```bash
cd sites/landing
docker build -t lustres-landing .
docker run -p 8080:80 lustres-landing
# Visit http://localhost:8080
```

## CI

The GitHub Actions workflow (`.github/workflows/build-sites.yaml`) uses path-filtered matrix builds:
- Only changed sites are rebuilt on push to `main`
- `workflow_dispatch` builds all 3 sites
- Images are tagged with the short commit SHA
- The `sunnepah-bot` commits updated image tags back to the orbit repo
