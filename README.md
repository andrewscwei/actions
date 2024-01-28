# GitHub Workflows

This repository contains reusable GitHub workflows.

## Workflows

## `node-build`

Builds a Nodejs project.
  - Infers Node version from `.node-version` file at project root
  - Caches NPM modules
  - Option to specify build command (defaults to `npm run build`)
  - Option to specify test command (defaults to `npm test`)
  - Option to upload built files as artifacts

### Usage

```yml
jobs:
  build:
    uses: andrewscwei/workflows/.github/workflows/node-build.yml@v1
    with:
      artifacts-name: <string="build-artifacts"> # Artifacts name
      artifacts-path: <string?> # Artifacts path (relative to working directory)
      build-command: <string="npm run build"> # Build command
      service-image: <string?> # Image of the service to use
      service-port: <string="8080:8080"> # Port mapping of the service (i.e. <host_port>:<service_container_port>)
      skip-tests: <boolean=false> # Specifies if tests should run
      test-command: <string="npm test"> # Command for running tests
    secrets:
      gh-access-token: <string?> # GitHub access token for checking out private repos
```

## `docker-build`

Builds a Docker image.
  - Caches multi-step Docker builds
  - Looks for and builds `prod` multi-step target
  - Option to run a test command against `test` multi-step target
  - Option to push the image to a registry (defaults to Docker Hub)

### Usage

```yml
deploy:
  uses: andrewscwei/workflows/.github/workflows/docker-build.yml@v1
  with:
    artifacts-name: <string="build-artifacts"> # Artifacts name
    artifacts-path: <string?> # Artifacts path (relative to working directory)
    build-args: <string?> # List of build-time variables
    build-secrets: <string?> # List of build-time secrets
    push: <boolean=false> # Specifies if pushing image to registry
    image-name: <string="${{ github.repository }}"> # Docker image base name
    image-tag-suffix: <string?> # Docker image tag suffix
    registry: <string="hub.docker.com"> # Registry path (required if `push` is `true`)
    test-command: <string?> # Command for running tests
```

## `npm-deploy`

Publishes an NPM project to an NPM registry and creates a release on GitHub.
  - Option to download artifacts prior to deploying
  - Option to execute a command prior to deploying

### Usage

```yml
deploy:
    uses: andrewscwei/workflows/.github/workflows/npm-deploy.yml@v1
    with:
      artifacts-name: <string="build-artifacts"> # Name of the artifacts to download
      artifacts-path: <string?> # Path (relative to working directory) to download artifacts to
      create-release: <boolean=false> # Specifies if a release should be created
      predeploy-command: <string?> # Command to run before deploying
      registry: <string="https://registry.npmjs.org"> # NPM package registry URL
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
    uses: andrewscwei/workflows/.github/workflows/gh-pages-deploy.yml@v1
    with:
      artifacts-name: <string="build-artifacts"> # Name of the artifacts to download
      artifacts-path: <string?> # Path (relative to working directory) to download artifacts to
      branch-name: <string="gh-pages"> # Branch for GitHub Pages
      create-release: <boolean=false> # Specifies if a release should be created
      deploy-path: <string=".gh-pages"> # Path to deploy to GitHub Pages
      predeploy-command: <string?> # Command to run before deploying to GitHub Pages
    secrets:
      gh-access-token: <string?> # GitHub access token for checking out private repos
```