Model Context Protocol (MCP)


[Model Context Protocol](https://modelcontextprotocol.io/introduction) (MCP) is
an open protocol that standardizes how applications provide context and
additional functionality to large language models. MCP functions as a
client-server protocol, where the client, for example an application like
Gordon, sends requests, and the server processes those requests to deliver the
necessary context to the AI. This context may be gathered by the MCP server by
executing code to perform an action and retrieving the result, calling external
APIs, or other similar operations.

Gordon, along with other MCP clients like Claude Desktop or Cursor, can interact
with MCP servers running as containers.

{{< grid >}}



- [Built-in tools in Gordon](https://docs.docker.com/ai/gordon/mcp/built-in-tools/)

- [Configure MCP servers with YAML](https://docs.docker.com/ai/gordon/mcp/yaml/)
