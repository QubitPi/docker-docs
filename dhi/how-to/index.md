How-tos


This section provides practical, step-by-step guidance for working with Docker
Hardened Images (DHIs). Whether you're evaluating DHIs for the first time or
integrating them into a production CI/CD pipeline, these topics walk you
through each phase of the adoption journey, from discovery to debugging.

To help you get started and stay secure, the topics are organized around the
typical lifecycle of working with DHIs.

## Lifecycle flow

1. Explore available images and metadata in the DHI catalog.
2. Mirror trusted images into your namespace or registry.
3. Adopt DHIs in your workflows by pulling, using in development and CI, and
   migrating existing applications to use secure, minimal base images.
4. Analyze images by verifying signatures, SBOMs, and provenance, and scanning
   for vulnerabilities.
5. Enforce policies to maintain security and compliance.
6. Debug containers based on DHIs without modifying the image.

Each of the following topics aligns with a step in this lifecycle, so you can progress
confidently through exploration, implementation, and ongoing maintenance.

## Step-by-step topics

{{< grid
  items="grid_howto"
>}}


- [Explore Docker Hardened Images](https://docs.docker.com/dhi/how-to/explore/)

- [Mirror a Docker Hardened Image repository](https://docs.docker.com/dhi/how-to/mirror/)

- [Use a Docker Hardened Image](https://docs.docker.com/dhi/how-to/use/)

- [Verify a Docker Hardened Image](https://docs.docker.com/dhi/how-to/verify/)

- [Scan Docker Hardened Images](https://docs.docker.com/dhi/how-to/scan/)

- [Enforce Docker Hardened Image usage with policies](https://docs.docker.com/dhi/how-to/policies/)

- [Migrate an existing application to use Docker Hardened Images](https://docs.docker.com/dhi/how-to/migrate/)

- [Debug a Docker Hardened Image container](https://docs.docker.com/dhi/how-to/debug/)
