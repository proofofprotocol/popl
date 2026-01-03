# Validation Principles

Core principles for POPL validation sessions.

## 1. Evidence First

> Capture raw data before summarizing.

- `events.json` is primary evidence
- RUNLOG.md is secondary context
- Never rely on memory or reconstruction

## 2. No Simulation

> Real protocol communication only.

- Connect to actual MCP servers
- Use real network conditions
- Document failures as evidence (they're valuable)

## 3. Logs Over Summaries

> Raw logs trump interpretations.

- Keep full JSON-RPC payloads
- Don't edit or filter events.json
- Summaries go in RUNLOG.md, not evidence files

## 4. Always Commit

> If it happened, it's in Git.

- Commit immediately after session ends
- Sandbox instances are ephemeral
- No commit = no evidence

## 5. One Session = One Entry

> Each validation session gets its own POPL entry.

- Separate directories: `session-YYYY-MM-DD-<target>/`
- Separate POPL.yml per session
- Don't merge unrelated sessions

## 6. Hash Everything

> Content hashes enable verification.

- SHA-256 for all artifacts
- Record hashes in POPL.yml
- Verify hashes match after notarization

## 7. Timestamp via Notarization

> Git commits are not sufficient for time proof.

- IPFS provides content addressing
- Hedera HCS provides decentralized timestamp
- Both required for Level 1

## 8. Failures Are Evidence

> A failed validation is still a valid observation.

- Document error messages
- Capture partial events.json
- Record environment details
- Example: "uvx ENOENT" is evidence of tooling requirements
