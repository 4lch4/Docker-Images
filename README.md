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



[0]: https://hub.docker.com/_/node
[1]: https://docs.doppler.com/docs/cli
[2]: https://hub.docker.com/_/node/tags?page=1&name=lts
[3]: https://github.com/4lch4/Docker-Images/tree/main/Node
[4]: https://hub.docker.com/repository/docker/4lch4/node/general
[5]: https://git.4lch4.io/4lch4/Doppler-And-Docker-Starter
