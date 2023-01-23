[![GitHub Workflow Status][9]][10] [![code style: prettier][11]][12] [![GitHub License][13]][14] [![Discord][18]][19]

[![Docker Image Version (latest semver)][16]][17] [![Docker Image Size (tag)][15]][8]

# Parental Docker Images

While the name is a bit odd, this repository contains the files for creating Docker images that are to be used as the base of another Docker image.

For example, the first one that I'm adding/creating is in the `./Node` directory that extends the official [node:lts][0] image by adding the [Doppler CLI][1] to the image.

## Images

If you would like to read some more information on the available images then refer to the README within each directory.

- [Node][20]

[0]: https://hub.docker.com/_/node
[1]: https://docs.doppler.com/docs/cli
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
[20]: ./Node/README.md
