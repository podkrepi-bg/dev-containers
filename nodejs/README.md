# Setup for NodeJS development
Currently, all modules within Podkrepi.bg are built using NodeJS 16. [Yarn](https://yarnpkg.com/) is used as a package manager.

- [Visual Studio Code setup](#visual-studio-code-setup)
- [Github Workflows](#github-workflows)

## Visual Studio Code setup
The easiest way to start developing NodeJS modules for Podkrepi.bg is by using [Visual Studio Code](https://code.visualstudio.com/download). Make sure the [Remote Containers extension](https://code.visualstudio.com/docs/remote/containers) is installed. It provides an easy way to configure a container as a [development environment](https://code.visualstudio.com/docs/remote/containers). This can be done by adding a `.devcontainer/devcontainer.json` to the root of the workspace. In most cases, it is sufficient to copy the contents of this example:

```json
{
	"name": "NodeJS",
    "image": "ghcr.io/podkrepi-bg/nodejs-devcontainer:v1.1.0",
	"forwardPorts": [], // Forward ports
	"containerEnv": {
		"DATABASE_URL": "postgres://postgres:postgrespass@host.docker.internal:5432/postgres?schema=api" // Custom env vars
	},
	"postStartCommand": "yarn", // Install dependencies
	"extensions": [
		"ms-azuretools.vscode-docker",
		"nrwl.angular-console",
		"esbenp.prettier-vscode",
		"firsttris.vscode-jest-runner",
		"dbaeumer.vscode-eslint"
	],
	"mounts": [
		"source=/var/run/docker.sock,target=/var/run/docker.sock,type=bind"
	]
}
```

## Github Workflows
TODO




