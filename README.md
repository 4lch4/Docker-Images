# Parental Docker Images

While the name is a bit odd, this repository/directory is where I store any `Dockerfile` that, when built into an image, can be used as the parent image for other projects built with Docker.

## Node

For example, the first one that I'm adding/creating is the `./Node` image. It's an extension of the [node:lts][0] image that installs the [Doppler CLI][1] to the image.


[0]: https://hub.docker.com/_/node
[1]: https://docs.doppler.com/docs/cli
