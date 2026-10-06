# Lecture 100 - Querying catalogdb Through MCP

One prompt that no amount of code reading could answer, and one configuration snippet for the place this server actually belongs.

---

## Step 1 - A question nobody could answer from the code

**Where:** the `claude` session, after the Postgres MCP server is connected.

**What it does:** Claude queries the live database and answers with real rows. This is what an MCP server buys you: facts from a running system, not inferences from source files.

```text
Using the Postgres MCP tools, how many products are in catalogdb, and what are the three most expensive ones?
```

---

## Step 5 - Where to put it instead

**Where:** `~/.claude.json`, your personal configuration. This is not a prompt to send; it is the snippet you paste there after removing the server from the repository.

**What it does:** A database server is a personal tool, not a team rule. The connection string stays in an environment variable, so nothing secret is written into a file.

```text
mcpServers:
  - postgres-catalogdb:
      command: npx
      args: ["-y", "@modelcontextprotocol/server-postgres", "${CATALOGDB_CONNECTION}"]
```
