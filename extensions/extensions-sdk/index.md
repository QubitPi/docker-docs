Overview of the Extensions SDK


The resources in this section help you create your own Docker extension.

The Docker CLI tool provides a set of commands to help you build and publish your extension, packaged as a 
specially formatted Docker image.

At the root of the image filesystem is a `metadata.json` file which describes the content of the extension. 
It's a fundamental element of a Docker extension.

An extension can contain a UI part and backend parts that run either on the host or in the Desktop virtual machine.
For further information, see [Architecture](architecture/_index.md).

You distribute extensions through Docker Hub. However, you can develop them locally without the need to push 
the extension to Docker Hub. See [Extensions distribution](extensions/DISTRIBUTION.md) for further details.

{{% include "extensions-form.md" %}}

{{< grid >}}



- [The build and publish process](https://docs.docker.com/extensions/extensions-sdk/process/)

- [Quickstart](https://docs.docker.com/extensions/extensions-sdk/quickstart/)

- [Part one: Build](https://docs.docker.com)

- [Part two: Publish](https://docs.docker.com/extensions/extensions-sdk/extensions/)

- [Extension architecture](https://docs.docker.com/extensions/extensions-sdk/architecture/)

- [UI styling overview for Docker extensions](https://docs.docker.com/extensions/extensions-sdk/design/)

- [Developer Guides](https://docs.docker.com)

- [Developer SDK tools](https://docs.docker.com)
