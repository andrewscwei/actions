# docker-run

Executes a command while running a Docker container.

## Usage

Example usage to run tests against a Docker image.

```yml
steps:
  - uses: andrewscwei/actions/docker-run@v2
    with:
      image: ghcr.io/<owner>/<repo>:latest
      command: npm test
      registry: ghcr.io
```

### Inputs

| Input | Required | Default | Description |
| ----- | -------- | ------- | ----------- |
| `command` | `true` | | Command to execute |
| `container-port` | `false` | `${{ inputs.port }}` | Container port to expose, defaults to `port` |
| `image` | `true` | | Docker image to test |
| `port` | `false` | `8080` | The port in which the app is served on |
| `registry` | `false` | | URL of the registry of the Docker container |
| `registry-user` | `false` | | Username for the registry |
| `registry-password`| `false` | | Password for the registry |

### Outputs

This action does not produce any outputs.
