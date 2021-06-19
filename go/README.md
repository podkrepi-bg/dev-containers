# Setup for Go development
Currently, all modules within Podkrepi.bg are built using Go 1.16. [Taskfile](https://taskfile.dev) is used to specify the build steps for each module and [golangci-lint](https://golangci-lint.run/) is used for linting the code.

- [Visual Studio Code setup](#visual-studio-code-setup)
- [Minimal Taskfile](#minimal-taskfile)
- [Github Workflows](#github-workflows)

## Visual Studio Code setup
The easiest way to start developing Go modules for Podkrepi.bg is by using [Visual Studio Code](https://code.visualstudio.com/download). It provides an easy way to configure a container as a [development environment](https://code.visualstudio.com/docs/remote/containers). This can be done by adding a `.devcontainer/devcontainer.json` to the root of the workspace. In most cases, it is sufficient to copy the contents of this example:

```json
{
	"name": "Go",
	"context": "..",
	"image": "TODO",
	"settings": {
		"go.useLanguageServer": true
	},
	"extensions": [
		"golang.go",
		"ms-azuretools.vscode-docker"
	],
	"mounts": [
		"source=/var/run/docker.sock,target=/var/run/docker.sock,type=bind",
		"source=${env:GOPATH}/pkg/mod/cache:/go/pkg/mod/cache"
	],
	"remoteUser": "vscode"
}
```

## Minimal Taskfile
TODO

## Github Workflows
TODO




