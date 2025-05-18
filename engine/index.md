Docker Engine


Docker Engine is an open source containerization technology for building and
containerizing your applications. Docker Engine acts as a client-server
application with:

- A server with a long-running daemon process
  [`dockerd`](/reference/cli/dockerd).
- APIs which specify interfaces that programs can use to talk to and instruct
  the Docker daemon.
- A command line interface (CLI) client
  [`docker`](/reference/cli/docker/).

The CLI uses [Docker APIs](/reference/api/engine/_index.md) to control or interact with the Docker
daemon through scripting or direct CLI commands. Many other Docker applications
use the underlying API and CLI. The daemon creates and manages Docker objects,
such as images, containers, networks, and volumes.

For more details, see
[Docker Architecture](/get-started/docker-overview.md#docker-architecture).

{{< grid >}}

## Licensing

The Docker Engine is licensed under the Apache License, Version 2.0. See
[LICENSE](https://github.com/moby/moby/blob/master/LICENSE) for the full license
text. 

However, for commercial use of Docker Engine obtained via Docker Desktop within larger enterprises (exceeding 250 employees OR with annual revenue surpassing $10 million USD), a [paid subscription](https://www.docker.com/pricing/) is required.



- [Install Docker Engine](https://docs.docker.com/engine/install/)

- [Storage](https://docs.docker.com/engine/storage/)

- [Networking overview](https://docs.docker.com/engine/network/)

- [Containers](https://docs.docker.com)

- [CLI](https://docs.docker.com)

- [Docker daemon configuration overview](https://docs.docker.com/engine/daemon/)

- [Manage resources](https://docs.docker.com)

- [View container logs](https://docs.docker.com/engine/logging/)

- [Docker Engine security](https://docs.docker.com/engine/security/)

- [Swarm mode](https://docs.docker.com/engine/swarm/)

- [Deprecated Docker Engine features](https://docs.docker.com/engine/deprecated/)

- [Docker Engine managed plugin system](https://docs.docker.com/engine/extend/)

- [Release notes](https://docs.docker.com)
