# `andrewscwei/actions/docker-run`

Executes a command while running a Docker container.

```yml
steps:
  - name: Docker Concurrently
    uses: andrewscwei/actions/docker-run@v2
    with:
      command: <string>
      container-port: <string?>
      image: <string>
      port: <string?>
```

## Usage

Example usage to run tests against a Docker image.
```yml
# GitHub Actions workflow
...
jobs:
  build:
    name: Test
    runs-on: ubuntu-latest
    steps:
      - name: Test
        uses: andrewscwei/actions/docker-run@v2
        with:
          image: ghcr.io/<owner>/<repo>:latest
          command: npm test
```
