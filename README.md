# Project Sandstar MCP marketplace

One marketplace for both plugins. Each plugin lives in its own server repo;
this file only points at them.

| Plugin | Server | Source |
|---|---|---|
| `fantom-mcp` | Fantom MCP server, `:3848` | `FantomMcpServer` repo, `claudePlugin/dist` |
| `axon-mcp` | Axon MCP server, `:3847` | `AxonMcpServer` repo, `claudePlugin/dist` |

## Install

```bash
claude plugin marketplace add <this repo's git url>
claude plugin install fantom-mcp@project-sandstar-mcp
claude plugin install axon-mcp@project-sandstar-mcp
```

Install one or both. Both plugins reach their server through mcp-proxy on
`:9191` by default. To use another host, set the plugin options:

```bash
claude plugin configure fantom-mcp@project-sandstar-mcp   # mcp_url, server_url, report_token
claude plugin configure axon-mcp@project-sandstar-mcp     # mcp_url, server_url
```

The Fantom plugin needs a report token for its hooks: create one in the
Fantom dashboard (Indexing > Report token).

## Update

```bash
claude plugin marketplace update project-sandstar-mcp
```

Plugins install from the `main` branch of each server repo. A plugin change
is live for others only after its `claudePlugin/dist` is rebuilt, committed
and pushed in that repo.

## Do not install from two marketplaces

Each server repo is also a marketplace by itself (`fantom-mcp`, `axon-mcp`).
Pick one source per plugin; with both, you get the same tools twice.
