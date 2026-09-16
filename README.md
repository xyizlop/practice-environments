## Deploying Site to Github Pages

The `index.html` file:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>devstuffs CI/CD practice</title>
  <style>
    body { font-family: system-ui, sans-serif; background: #0B0E14; color: #E4E2DC; display: flex; align-items: center; justify-content: center; height: 100vh; margin: 0; }
    .card { text-align: center; }
    code { color: #E8A33D; }
  </style>
</head>
<body>
  <div class="card">
    <h1>Hello from devstuffs 👋</h1>
    <p>This page was deployed by GitHub Actions.</p>
    <p><code id="target">deployment target: unknown</code></p>
  </div>
</body>
</html>
```

## Steps to Deploy

- Checkout Repo → `actions/checkout` (Checkout Repo)
- [Optional] Setup Page → `actions/configure-pages` (enable Pages and extract various metadata about a site)
- Upload Artifacts (Must be tarball directory, file not accepted so `index.html` is placed under `_site`) → `actions/upload-pages-artifact` (Default `path` is `_site`)
- Deploy Page → `actions/deploy-pages` (Accepts the tarball uploaded by previous step, Required permissions: `contents: read`, `pages: write`, `id-token: write`)

## Add Review

Go to Repository **Settings → Environments → github-pages → Deployment protection rules → Check Required reviewers → Add by github username**

This means reviewers hav to review and then deploy.