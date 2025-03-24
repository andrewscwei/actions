# `andrewscwei/actions/node-build` ![GitHub Release](https://img.shields.io/github/v/release/andrewscwei/actions?label=latest)

Builds and tests a Node.js project:

- Infers Node version from `.node-version` / `.tool-versions` / `.nvmrc` file at project root
- Caches NPM modules
- Option to specify build command (defaults to `npm run build`)
- Option to specify prebuild command
- Option to specify postbuild command
- Option to upload built files as artifact

## Usage

```yml
steps:
  - uses: andrewscwei/actions/node-build@v2
    with:
      artifact-path: build/
      build-command: npm run build
      prebuild-command: npm run unit
```

### Inputs

| Input | Required | Default | Description |
| ----- | -------- | ------- | ----------- |
| `artifact-name` | `false` | `build-artifact` | Artifacts name |
| `artifact-path` | `false` | | Artifacts path (relative to working directory) |
| `build-command` | `false` | `npm run build` | Build command (defaults to `<package_manager> run build`) |
| `node-version-file` | `false` | | Node.js version file (automatically inferred if unprovided) |
| `package-manager` | `false` | | Package manager to use (`npm`, `yarn` or `pnpm`, automatically inferred if unprovided) |
| `postbuild-command` | `false` | | Command to run after building |
| `prebuild-command` | `false` | | Command to run before building |

### Outputs

| Output | Description |
| ------ | ----------- |
| `artifact-name` | Name of the uploaded artifacts |
| `artifact-path` | Path of the uploaded artifacts (relative to working directory) |
