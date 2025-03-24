# `andrewscwei/actions/wait-for` ![GitHub Release](https://img.shields.io/github/v/release/andrewscwei/actions?label=latest)

Runs a command and waits for the command to yield a result (as described by a regex pattern):

- Executes a specified command
- Waits for the command output to match a regex pattern
- Configurable interval between command executions
- Configurable timeout for the command execution

## Usage

Example usage:

```yml
steps:
  - uses: andrewscwei/actions/wait-for@v2
    with:
      command: "curl -s http://example.com"
      result: "HTTP/2 200"
      interval: 5
      timeout: 60
```

### Inputs

| Input | Required | Default | Description |
| ----- | -------- | ------- | ----------- |
| `command` | `true` | | The command to execute |
| `result` | `true` | | The regex pattern of the result to wait for |
| `interval` | `true` | `2` | The interval in seconds between command executions |
| `timeout` | `true` | `30` | The timeout in seconds |

### Outputs

This action does not produce any outputs.
