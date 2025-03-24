# release

Publishes a GitHub release.

## Usage

```yml
steps:
  - uses: andrewscwei/actions/release@v2
    with:
      version: v1.0.0
```

### Inputs

| Input | Required | Default | Description |
| ----- | -------- | ------- | ----------- |
| `draft` | `false` | `false` | Specifies if the release should be a draft |
| `prerelease` | `false` | `false` | Specifies if the release should be a prerelease |
| `version` | `true` | | Release version |

### Outputs

This action does not produce any outputs.
