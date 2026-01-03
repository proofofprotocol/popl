# Genspark Sandbox Instructions

How to run POPL validation sessions in Genspark sandbox.

## Overview

Genspark provides isolated sandbox environments for MCP server validation. Sandboxes are **ephemeral** - all data is lost when the session ends.

**Critical:** Always commit and push before ending the sandbox session.

## Prerequisites

- Genspark account with sandbox access
- GitHub personal access token (for pushing)
- Target MCP server package name

## Step-by-Step

### 1. Launch Sandbox

Start a new Genspark sandbox session. Note the environment details for RUNLOG.md.

### 2. Clone Repositories

```bash
# Clone proofscan (evidence store)
git clone https://github.com/proofofprotocol/proofscan.git
cd proofscan

# Configure git
git config user.email "your-email@example.com"
git config user.name "Your Name"
```

### 3. Install proofscan

```bash
npm install -g .
# or
npm link
```

### 4. Configure Connector

```bash
# Add MCP server as connector
pfscan connectors add <target> --from-mcp-json '{
  "command": "npx",
  "args": ["-y", "@example/mcp-server-name"]
}'

# Verify
pfscan connectors list
```

### 5. Run Validation Session

```bash
# Start scan
pfscan scan start <target>

# Use shell for interactive exploration
pfscan shell

# In shell:
> tool ls
> send <tool-name> {"param": "value"}
> show @last --json
```

### 6. Export Artifacts

```bash
# Create session directory
mkdir -p validation/session-$(date +%Y-%m-%d)-<target>

# Export events
pfscan events export --format json > validation/session-.../events.json

# Export tree
pfscan tree --json > validation/session-.../tree.json

# Create RUNLOG.md manually or copy template
```

### 7. Create POPL.yml

Copy template from [popl/templates/POPL.yml](https://github.com/proofofprotocol/popl/blob/main/templates/POPL.yml) and fill in:

- entry_id
- title
- observed_at
- target details
- artifact hashes (use `sha256sum`)

### 8. Calculate Hashes

```bash
cd validation/session-.../
sha256sum events.json tree.json RUNLOG.md
```

Update POPL.yml with hashes.

### 9. Commit and Push

```bash
git add validation/session-.../
git commit -m "validation: add session <target> (<date>)"
git push origin main
```

### 10. Notarize (Optional - Level 1)

If inscribe-mcp is available:

```bash
pfscan shell
> inscribe @last
```

Update POPL.yml with notarization details.

## Checklist

See [execution-checklist.md](execution-checklist.md) for a copy-paste checklist.

## Troubleshooting

### uvx not found (ENOENT)

Genspark sandbox may not have `uvx`. Use `npx` instead:

```bash
# Instead of: uvx mcp-server-time
# Use: npx -y @anthropic-ai/mcp-server-time
```

This is a known limitation. Document it as evidence.

### npm install fails

Try with `--legacy-peer-deps`:

```bash
npm install --legacy-peer-deps
```

### Git push fails

Ensure PAT is configured:

```bash
git remote set-url origin https://<token>@github.com/proofofprotocol/proofscan.git
```

## Reference

- Spec repository: [proofofprotocol/popl](https://github.com/proofofprotocol/popl)
- Evidence store: [proofofprotocol/proofscan](https://github.com/proofofprotocol/proofscan)
- Validation playbook: [docs/validation-playbook.md](https://github.com/proofofprotocol/proofscan/blob/main/docs/validation-playbook.md)
