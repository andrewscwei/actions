# `andrewscwei/actions/gh-pages-deploy`

Deploys to GitHub Pages:

- Option to download artifact prior to deploying
- Option to execute a command before deploying
- Option to execute a command after deploying

```yml
steps:
  - name: Deploy
    uses: andrewscwei/actions/gh-pages-deploy@v1
    with:
      artifact-name: <string="build-artifact">
      artifact-path: <string?>
      branch-name: <string="gh-pages">
      cname: <string?>
      deploy-path: <string=".gh-pages">
      gh-access-token: <string?>
      postdeploy-command: <string?>
      predeploy-command: <string?>
```
