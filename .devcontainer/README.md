# README for Docker and Dev Containers Setup

## Install Dev Containers plugin

- Name: Dev Containers
- Id: ms-vscode-remote.remote-containers
- Description: Open any folder or repository inside a Docker container and take advantage of Visual Studio Code's full feature set.
- Version: 0.338.1
- Publisher: Microsoft
- [VS Marketplace Link](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Dev Containers tutorial:

https://code.visualstudio.com/docs/devcontainers/tutorial

VSCode will read this folder and set up the docker container dev env.

## How it works

This next section describes in more detail how the Dev Containers extension sets up and configures your containers.

The Dev Containers extension uses the files in the .devcontainer folder, namely devcontainer.json, and an optional Dockerfile or docker-compose.yml, to create your dev containers.

In the example we just explored, the project has a .devcontainer folder with a devcontainer.json inside. The devcontainer.json uses the image mcr.microsoft.com/devcontainers/javascript-node:0-18. You can explore this image in greater detail in the devcontainers/images repo.

First, your image is built from the supplied Dockerfile or image name, which would be mcr.microsoft.com/devcontainers/javascript-node:0-18 in this example. Then a container is created and started using some of the settings in the devcontainer.json. Finally your Visual Studio Code environment is installed and configured again according to settings in the devcontainer.json. For example, the dev container in this example installs the streetsidesoftware.code-spell-checker extension.

Note: Additional configuration will already be added to the container based on what's in the base image. For example, we see the streetsidesoftware.code-spell-checker extension above, and the container will also include "dbaeumer.vscode-eslint" as that's part of mcr.microsoft.com/devcontainers/typescript-node. This happens automatically when pre-building using devcontainer.json, which you may read more about in the pre-build section.

Once all of this is done, your local copy of Visual Studio Code connects to the Visual Studio Code Server running inside of your new dev container.

## devcontainer.json

The devcontainer.json is basically a config file that determines how your dev container gets built and started.

You can review the [full list of devcontainer.json options](https://containers.dev/implementors/json_reference/).

## Dockerfile

Dockerfile is the file for docker to build the container step by step, layer by layer.