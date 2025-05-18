MCP


## What is MCP?

[Model Context Protocol](https://modelcontextprotocol.io/introduction) (MCP) is
an open protocol that standardizes how applications provide context and extra
functionality to large language models. MCP functions as a client-server
protocol, where the client, for example an application like Gordon, sends
requests, and the server processes those requests to deliver the necessary
context to the AI. This context may be gathered by the MCP server by executing
some code to perform an action and getting the result of the action, calling
external APIs, etc.

Gordon, along with other MCP clients like Claude Desktop or Cursor, can interact
with MCP servers running as containers.

{{< grid >}}


- [Built-in tools](https://docs.docker.com/ai/gordon/mcp/built-in-tools/)

- [Gordon as an MCP server](https://docs.docker.com/ai/gordon/mcp/gordon-mcp-server/)

- [YAML configuration](https://docs.docker.com/ai/gordon/mcp/yaml/)
