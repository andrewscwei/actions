# GitHub Workflows

This repository contains reusable GitHub workflows.

## Actions

## `docker-build-push`

Builds and optionally pushes a container image to a registry:
  - Sets up Docker Buildx
  - Caches multi-step Docker builds
  - Option to upload built artifact inside image as artifact
  - Option to upload built image as artifact
  - Option to push the image to a registry (defaults to Docker Hub)

### Usage

```yml
steps:
  - name: Build
    uses: andrewscwei/actions/docker-build-push@v1
    with:
      build-artifact-dir: <string?>
      build-artifact-name: <string="build-artifact">
      build-artifact-working-dir: <string="/var/app">
      build-args: <string?>
      build-secrets: <string?>
      dockerfile-path: <string="Dockerfile">
      github-token: <string?>
      image-artifact-dir: <string?>
      image-artifact-name: <string="image-artifact">
      image-name: <string=${{ github.repository }}>
      image-tag-suffix: <string?>
      push: <string="false">
      registry: <string?>
```

## `node-build`

Builds and tests a Node.js project:
  - Infers Node version from `.node-version` file at project root
  - Caches NPM modules
  - Option to specify build command (defaults to `npm run build`)
  - Option to specify prebuild command
  - Option to specify postbuild command
  - Option to upload built files as artifact

### Usage

```yml
steps:
  - name: Build
    uses: andrewscwei/actions/node-build@v1
    with:
      artifact-name: <string="build-artifact">
      artifact-path: <string?>
      build-command: <string="npm run build">
      postbuild-command: <string?>
      prebuild-command: <string?>
```

## `npm-deploy`

Publishes to an NPM registry:
  - Option to download artifact prior to deploying

### Usage

```yml
steps:
  - name: Deploy
    uses: andrewscwei/actions/npm-deploy@v1
    with:
      artifact-name: <string="build-artifact">
      artifact-path: <string?>
      npm-auth-token: <string?>
      registry: <string="https://registry.npmjs.org">
```

## `gh-pages-deploy`

Deploys to GitHub Pages:
  - Option to download artifact prior to deploying
  - Option to execute a command before deploying
  - Option to execute a command after deploying

### Usage

```yml
steps:
  - name: Deploy
    uses: andrewscwei/actions/gh-pages-deploy@v1
    with:
      artifact-name: <string="build-artifact">
      artifact-path: <string?>
      branch-name: <string="gh-pages">
      deploy-path: <string=".gh-pages">
      gh-access-token: <string?>
      postdeploy-command: <string?>
      predeploy-command: <string?>
```
