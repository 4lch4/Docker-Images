[![GitHub Workflow Status][9]][10] [![code style: prettier][11]][12] [![GitHub License][13]][14] [![Discord][18]][19]

[![Docker Image Version (latest semver)][16]][17] [![Docker Image Size (tag)][15]][8]

# Parental Docker Images

While the name is a bit odd, this repository contains the files for creating Docker images that are to be used as the base of another Docker image.

For example, the first one that I'm adding/creating is in the `./Node` directory that extends the official [node:lts][0] image by adding the [Doppler CLI][1] to the image.

## Images

Now, let's break down each of the images this repository makes available.

### Node

- [Parent Image][0]
- [Docker Hub][4]
- [Git Repository][3]

This image is the one mentioned in the initial example, and it starts with the official [Node image][0] that's tagged as [`lts`][2] and then adds the [Doppler CLI][1] so it can be used for secret management.

#### When/How Often Is It Updated?

The image is built and pushed to Docker Hub when any of the following events occur:

- When a new change was pushed to the remote repository.
- Once a day when it's 08:00 UTC or 02:00 CST.
- When a developer kicks off a manual run via the GitHub UI (aka `workflow_dispatch`).

#### Using the Doppler CLI

In order to use the **Doppler CLI** you _must_ pass a [Service Token](https://docs.doppler.com/docs/service-tokens) with, at least, read access to the config you wish to use. Here is an example:

```bash
docker run -d --name=doppler-test \
            -e DOPPLER_TOKEN="doppler-service-token-here" \
            image-name-here
```

_NOTE: I also created a [CLI app](#cli-utility) to do this for you. If you're interested, I cover it in the following section._

### CLI Utility

- [Git Repository][5]

As mentioned above, in order to use the Doppler CLI you must pass a service token with at least read permissions for the config to be used. To make this easier, I've created a small CLI application, **Doppler And Docker Starter** (`dads`), that will run a docker image that uses Doppler under the hood. Once it's installed on your machine (instructions need to be added) you can start a container like so:

```bash
#dads <app-name> <img-name> [doppler-token]

# Start a container named app-name-here with the image-name here Docker image.
# The lack of a doppler token option means the app will search for a .env file
# in the current directory and try to pull a DOPPLER_TOKEN variable from there.
dads app-name-here image-name

# Starts a container using the image-name Docker image, names the container
# app-name-here, and uses doppler-token-here as the Doppler Service Token.
dads app-name-here image-name doppler-token-here
```

## Building the Images

If you wish to build the images yourself then you have two options:

1. Use the [Taskfile CLI][6] ([installation instructions][7]) to use the Taskfile build commands.
2. Run the Docker build commands directly.

Whichever method you wish to use, navigate to that section next to continue.

### Taskfile CLI

If you have the Taskfile CLI installed them you can use any of the build commands to build the Docker images.

For example, if you wanted to build the node image then you'd run the following command from the root of the repository:

```bash
task build:node

# You can also use the build:node alias like so:
#task bn
```

### Docker Commands

If you don't have, or want, the Taskfile CLI installed then you can pull the Docker commands directly from the Taskfile.yml and run them in your terminal.

For example, if you wanted to build the node image then you'd run the following command from the root of the repository:

```bash
docker build -t 4lch4/node:latest -t 4lch4/node:1.0.0 ./Node
```


[0]: https://hub.docker.com/_/node
[1]: https://docs.doppler.com/docs/cli
[2]: https://hub.docker.com/_/node/tags?page=1&name=lts
[3]: https://github.com/4lch4/Docker-Images/tree/main/Node
[4]: https://hub.docker.com/repository/docker/4lch4/node/general
[5]: https://git.4lch4.io/4lch4/Doppler-And-Docker-Starter
[6]: https://taskfile.dev
[7]: https://taskfile.dev/installation
[8]: https://hub.docker.com/r/4lch4/node
[9]: https://img.shields.io/github/actions/workflow/status/4lch4/Docker-Images/node.yml?style=flat-square
[10]: https://github.com/4lch4/Docker-Images/actions/workflows/node.yml
[11]: https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square
[12]: https://github.com/prettier/prettier
[13]: https://img.shields.io/github/license/4lch4/Docker-Images?style=flat-square
[14]: https://choosealicense.com/licenses/gpl-3.0
[15]: https://img.shields.io/docker/image-size/4lch4/node/latest?label=node%20image%20size&style=flat-square
[16]: https://img.shields.io/docker/v/4lch4/node?label=node%20image%20latest%20version&style=flat-square
[17]: https://hub.docker.com/r/4lch4/node/tags
[18]: https://img.shields.io/discord/325504841541746688?color=7289DA&style=flat-square
[19]: https://discord.gg/W72x4Ks
