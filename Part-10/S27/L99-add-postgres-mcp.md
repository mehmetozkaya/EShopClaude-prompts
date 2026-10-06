# Lecture 99 - Adding the Postgres MCP Server

One prompt. Everything else typed in this lecture is a command (`/mcp`, `claude`) or a shell line, and those live in the lecture's On-Screen Action blocks, not in this library.

**Where:** the `claude` session at the `EShopClaude` root, with the application running under `aspire run`.

**What it does:** Claude finds the connection string, writes `.mcp.json`, and tells you what to do next. Read what it wrote before restarting: the connection string belongs in an environment variable, not committed into the file.

```text
Get the Postgres connection string for catalogdb from the Aspire dashboard, or from the console output of the running AppHost.

Add a Postgres MCP server to this repository's .mcp.json configured with that connection string, then tell me what to do to make its tools available.
```
