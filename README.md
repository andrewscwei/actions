# GitHub Workflows

This repository contains reusable GitHub workflows.

## Workflows

## `node-build`

Builds a Nodejs project.
  - Infers Node version from `.nvmrc` file at project root
  - Caches NPM modules
  - Executes `npm run build` to build the project
  - Executes `npm test` to run tests
  - Option to upload built files as artifacts

### Usage

```yml
jobs:
  build:
    uses: andrewscwei/workflows/.github/workflows/node-build.yml@master
    with:
      skip-tests: <boolean=false> # Specifies if tests should run
      artifacts-name: <string="build-artifacts"> # Artifacts name
      artifacts-path: <string?> # Artifacts path (relative to working directory)
      service-image: <string?> # Image of the service to use
      service-port: <string="8080:8080"> # Port mapping of the service (i.e. <host_port>:<service_container_port>)
    secrets:
      gh-access-token: <string?> # GitHub access token for checking out private repos
```

## `npm-deploy`

Publishes an NPM project to an NPM registry and creates a release on GitHub.
  - Option to download artifacts prior to deploying
  - Option to execute a command prior to deploying

### Usage

```yml
deploy:
    uses: andrewscwei/workflows/.github/workflows/npm-deploy.yml@master
    with:
      artifacts-name: <string="build-artifacts"> # Name of the artifacts to download
      artifacts-path: <string?> # Path (relative to working directory) to download artifacts to
    secrets:
      gh-access-token: <string?> # GitHub access token for checking out private repos
      npm-auth-token: <string?> # NPM auth token
```

## `gh-pages-deploy`

Publishes a directory to a branch used for GitHub Pages.
  - Option to download artifacts prior to deploying
  - Option to execute a command prior to deploying

### Usage

```yml
deploy:
    uses: andrewscwei/workflows/.github/workflows/gh-pages-deploy.yml@master
    with:
      artifacts-name: <string="build-artifacts"> # Name of the artifacts to download
      artifacts-path: <string?> # Path (relative to working directory) to download artifacts to
      branch-name: <string="gh-pages"> # Branch for GitHub Pages
      deploy-path: <string=".gh-pages"> # Path to deploy to GitHub Pages
      run-command: <string?> # Command to run before deploying to GitHub Pages
    secrets:
      gh-access-token: <string?> # GitHub access token for checking out private repos
```
