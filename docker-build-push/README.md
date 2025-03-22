# `andrewscwei/actions/docker-build-push`

Builds and optionally pushes a container image to a registry:

- Sets up Docker Buildx
- Caches multi-step Docker builds
- Option to upload built artifact inside image as artifact
- Option to upload built image as artifact
- Option to push the image to a registry (defaults to Docker Hub)

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
      registry-user: <string?>
      registry-password: <string?>
```

## Usage

Example usage for pushing to [GitHub Container Registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry):

```yml
# GitHub Actions workflow
...
jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Build
        uses: andrewscwei/actions/docker-build-push@v1
        with:
          push: true
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}
```
