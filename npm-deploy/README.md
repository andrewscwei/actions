# `andrewscwei/actions/npm-deploy` ![GitHub Release](https://img.shields.io/github/v/release/andrewscwei/actions?label=latest)

Publishes to an NPM registry:

- Option to download artifact prior to deploying

## Usage

```yml
steps:
  - uses: andrewscwei/actions/npm-deploy@v2
    with:
      registry: https://npm.pkg.github.com
```

### Inputs

| Input | Required | Default | Description |
| ----- | -------- | ------- | ----------- |
| `artifact-name` | `false` | `build-artifact` | Name of the artifact to download |
| `artifact-path` | `false` | | Path (relative to working directory) to download artifact to |
| `npm-auth-token` | `false` | `${{ github.token }}` | NPM auth token |
| `registry` | `false` | `https://registry.npmjs.org` | NPM package registry URL |

### Outputs

This action does not produce any outputs.
