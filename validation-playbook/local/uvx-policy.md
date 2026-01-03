# Local Execution Policy: uvx-based MCP Servers

## Policy

**uvx-based MCP servers are validated locally, not in Genspark sandbox.**

## Reason

Genspark sandbox does not include `uvx` (uv's tool runner). Attempts to run uvx-based servers result in `ENOENT` errors.

Example failure evidence: [proofscan/validation/session-2026-01-02-time/](https://github.com/proofofprotocol/proofscan/tree/main/validation/session-2026-01-02-time)

## uvx vs npx

| Tool | Package Manager | Genspark Support |
|------|-----------------|------------------|
| `uvx` | uv (Python) | No |
| `npx` | npm (Node.js) | Yes |

## Affected Servers

MCP servers that require uvx:

- `mcp-server-time` (when launched via `uvx mcp-server-time`)
- Other Python-based MCP servers using uv

## Workarounds

### Option 1: Use npx equivalent (if available)

Some servers have npm packages:

```bash
# Instead of: uvx mcp-server-time
npx -y @anthropic-ai/mcp-server-time
```

### Option 2: Validate locally

Run on a local machine with uv installed:

```bash
# Install uv
curl -LsSf https://astral.sh/uv/install.sh | sh

# Run server
uvx mcp-server-time
```

## Local Environment Requirements

For local validation:

- Pop!_OS 22.04 or similar Linux
- uv installed (`curl -LsSf https://astral.sh/uv/install.sh | sh`)
- proofscan installed
- Git configured

## POPL Entry Differences

When validating locally:

```yaml
observed:
  environment: "Local (Pop!_OS 22.04)"  # Not "Genspark Sandbox"
```

## Summary

| Server Type | Execution Environment |
|-------------|----------------------|
| npx-based | Genspark Sandbox (preferred) |
| uvx-based | Local machine (required) |
