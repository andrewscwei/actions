# `andrewscwei/actions/npm-deploy`

Publishes to an NPM registry:

- Option to download artifact prior to deploying

```yml
steps:
  - name: Deploy
    uses: andrewscwei/actions/npm-deploy@v2
    with:
      artifact-name: <string="build-artifact">
      artifact-path: <string?>
      npm-auth-token: <string?>
      registry: <string="https://registry.npmjs.org">
```
