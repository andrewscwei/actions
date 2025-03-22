# `andrewscwei/actions/node-build`

Builds and tests a Node.js project:

- Infers Node version from `.node-version` file at project root
- Caches NPM modules
- Option to specify build command (defaults to `npm run build`)
- Option to specify prebuild command
- Option to specify postbuild command
- Option to upload built files as artifact

```yml
steps:
  - name: Build
    uses: andrewscwei/actions/node-build@v2
    with:
      artifact-name: <string="build-artifact">
      artifact-path: <string?>
      build-command: <string="npm run build">
      postbuild-command: <string?>
      prebuild-command: <string?>
```
