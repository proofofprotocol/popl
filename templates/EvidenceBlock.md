# Evidence Block Template

Copy-paste this block into POP@AI articles or documentation to reference a POPL entry.

---

## Proof Badge

```
---
POPL Entry: popl-YYYY-MM-DD-target-001
Git Commit: proofofprotocol/proofscan@COMMIT_SHA
Environment: Genspark Sandbox
MCP Server: @example/mcp-server-name@1.0.0
---
Artifacts:
  - events.json (SHA256: abc123...)
  - tree.json (SHA256: def456...)
  - RUNLOG.md (SHA256: 789ghi...)
---
Notarization:
  IPFS: bafybei...
  Hedera HCS: 0.0.7503789-1234567890.123456789
---
```

---

## Compact Version (for inline use)

```
[POPL: popl-YYYY-MM-DD-target-001 | Git: abc123 | IPFS: bafybei... | HCS: 0.0.7503789]
```

---

## HTML Embed (for blogs)

```html
<div class="popl-badge">
  <strong>POPL Entry:</strong> popl-YYYY-MM-DD-target-001<br>
  <strong>Git:</strong> <a href="https://github.com/proofofprotocol/proofscan/commit/COMMIT_SHA">COMMIT_SHA</a><br>
  <strong>IPFS:</strong> <a href="https://ipfs.io/ipfs/bafybei...">bafybei...</a><br>
  <strong>Hedera:</strong> <a href="https://hashscan.io/mainnet/topic/0.0.7503789">0.0.7503789</a>
</div>
```

---

## Markdown Table

| Field | Value |
|-------|-------|
| Entry ID | `popl-YYYY-MM-DD-target-001` |
| Git Commit | [`abc123`](https://github.com/proofofprotocol/proofscan/commit/abc123) |
| Environment | Genspark Sandbox |
| MCP Server | `@example/mcp-server-name@1.0.0` |
| IPFS CID | `bafybei...` |
| Hedera HCS | `0.0.7503789-1234567890.123456789` |

---

## Usage Notes

1. Replace placeholder values with actual data from POPL.yml
2. Use the compact version for inline references
3. Use the full badge for article footers
4. Always include Git commit for Level 0 verification
5. Add IPFS/HCS for Level 1 verification
