# `andrewscwei/actions/docker-build-push` ![GitHub Release](https://img.shields.io/github/v/release/andrewscwei/actions?label=latest)

Builds and optionally pushes a container image to a registry:

- Sets up Docker Buildx
- Caches multi-step Docker builds
- Option to upload built artifact inside image as artifact
- Option to upload built image as artifact
- Option to push the image to a registry (defaults to Docker Hub)

## Usage

Example usage for pushing to [GitHub Container Registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry):

```yml
permissions:
  contents: read
  packages: write
steps:
  - uses: andrewscwei/actions/docker-build-push@v2
    with:
      push: true
      registry: ghcr.io
      username: ${{ github.actor }}
      password: ${{ secrets.GITHUB_TOKEN }}
```

### Inputs

| Input | Required | Default | Description |
| ----- | --------- | ------- | ----------- |
| `build-artifact-dir` | `false` | | Path to the built files directory in the container for artifact upload (newline-delimited string for each path, relative to the container's working directory) |
| `build-artifact-name` | `false` | `build-artifact` | Name of the artifact containing the built files to be uploaded |
| `build-artifact-working-dir` | `false` | `/var/app` | Absolute path to the container’s working directory to set the upload location for built files (newline-delimited string, no trailing slash) |
| `build-args` | `false` | | List of build-time arguments (newline-delimited string) |
| `build-secrets` | `false` | | List of build-time secrets (newline-delimited string) |
| `dockerfile-path` | `false` | `Dockerfile` | Path to the Dockerfile (relative to context) |
| `image-artifact-dir` | `false` | | Path to the directory containing the built image for artifact upload (absolute or relative to working directory) |
| `image-artifact-name` | `false` | `image-artifact` | Name of the artifact containing the built image to be uploaded |
| `image-name` | `false` | `${{ github.repository }}` | Docker image base name |
| `image-tag-suffix` | `false` | | Docker image tag suffix |
| `push` | `false` | `false` | Specifies if the built image should be pushed to the registry |
| `registry` | `false` | | URL of the registry to push to |
| `registry-user` | `false` | | Username for the registry |
| `registry-password` | `false` | | Password for the registry |

### Outputs

| Output | Description |
| ------ | ----------- |
| `build-artifact-dir` | Path to the directory of the uploaded artifact of built files (relative to working directory) |
| `build-artifact-name` | Name of the uploaded artifact of built files |
| `digest` | The digest of the built Docker image |
| `image` | The full name of built Docker image, including the registry, image name and tag (highest priority tag is used) |
| `image-artifact-dir` | Path to the directory of the uploaded artifact of the built image (absolute or relative to working directory) |
| `image-artifact-file` | Path to the uploaded artifact of the built image (absolute or relative to working directory) |
| `image-artifact-name` | Name of the uploaded artifact of the built image |
| `registry` | Full path to registry |
| `version` | The highest priority tag of the built Docker image |

## Permissions

Required permissions if using the automatically created `GITHUB_TOKEN` to authenticate to GitHub Container Registry:

```yml
permissions:
  contents: read
  packages: write
```
