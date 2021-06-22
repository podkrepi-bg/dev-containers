# Setup for Go development
Currently, all modules within Podkrepi.bg are built using Go 1.16. [Taskfile](https://taskfile.dev) is used to specify the build steps for each module and [golangci-lint](https://golangci-lint.run/) is used for linting the code.

- [Visual Studio Code setup](#visual-studio-code-setup)
- [Minimal Taskfile](#minimal-taskfile)
- [Github Workflows](#github-workflows)

## Visual Studio Code setup
The easiest way to start developing Go modules for Podkrepi.bg is by using [Visual Studio Code](https://code.visualstudio.com/download). Make sure the [Remote Containers extension](https://code.visualstudio.com/docs/remote/containers) is installed. It provides an easy way to configure a container as a [development environment](https://code.visualstudio.com/docs/remote/containers). This can be done by adding a `.devcontainer/devcontainer.json` to the root of the workspace. In most cases, it is sufficient to copy the contents of this example:

```json
{
	"name": "Go",
	"image": "ghcr.io/podkrepi-bg/go-devcontainer:v1.0.0",
	"settings": {
		"go.useLanguageServer": true
	},
	"extensions": [
		"golang.go",
		"ms-azuretools.vscode-docker"
	],
	"mounts": [
		"source=/var/run/docker.sock,target=/var/run/docker.sock,type=bind"
	]
}
```

## Minimal Taskfile
Create a `Taskfile.yml` in the root of the workspace. The configuration below contains a lint and a build step for a Go module. Consider specifying `generates` property for the tasks such that the tool can determine whether a step has to run or not based on the generated files' checksum. For more info see [this link](https://taskfile.dev/#/usage?id=prevent-unnecessary-work).

```yaml
# https://taskfile.dev

version: '3'

tasks:
  lint:
    cmds:
      - golangci-lint run
  build:
    cmds:
      - go build .
    silent: false
```

After the file is created, you can run the following command to lint the Go module:
```bash
task lint
```

## Github Workflows
TODO




