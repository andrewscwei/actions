# `andrewscwei/actions/gh-pages-deploy` ![GitHub Release](https://img.shields.io/github/v/release/andrewscwei/actions?label=latest)

Deploys to GitHub Pages:

- Option to download artifact prior to deploying
- Option to execute a command before deploying
- Option to execute a command after deploying

## Usage

```yml
steps:
  - uses: andrewscwei/actions/gh-pages-deploy@v2
    with:
      deploy-path: build/${{ github.event.repository.name }}
      predeploy-command: npm run build
```

### Inputs

| Input | Required | Default | Description |
| ----- | -------- | ------- | ----------- |
| `artifact-name` | `false` | `build-artifact` | Name of the artifact to download |
| `artifact-path` | `false` | | Path (relative to working directory) to download artifact to |
| `branch-name` | `false` | `gh-pages` | Branch for GitHub Pages |
| `cname` | `false` | | Custom subdomain for GitHub Pages |
| `deploy-path` | `false` | `.gh-pages` | Path to deploy to GitHub Pages |
| `github-token` | `false` | `${{ github.token }} | Custom GitHub token to use |
| `postdeploy-command` | `false` | | Command to run after deploying |
| `predeploy-command` | `false` | | Command to run before deploying |

### Outputs

| Output | Description |
| ------ | ----------- |
| `artifact-name` | Name of the downloaded artifact |
| `artifact-path` | Path to the downloaded artifact |
| `branch-name` | Branch used for GitHub Pages deployment |
| `cname` | Custom subdomain used for GitHub Pages |
| `deploy-path` | Path used for deployment to GitHub Pages |
| `gh-access-token` | GitHub access token used for checking out private repos |
| `postdeploy-command` | Command executed after deployment |
| `predeploy-command` | Command executed before deployment |
