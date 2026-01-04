# POPL Terminology

## Core Concepts

### Proof of Protocol
The philosophy that AI agent communication should be observable, recordable, and verifiable. Not a product, but a principle.

### POPL (Public Observable Proof Ledger)
The structured ledger format for recording validation sessions. Defines how evidence is organized, referenced, and notarized.

> **Origin name:** Proof of Protocol Ledger — The original name, emphasizing protocol-level evidence. As the project evolved toward public observability and publishable sanitized evidence, the name expanded to *Public Observable Proof Ledger*.

### POPL Entry
One validation session record. Contains:
- Manifest (POPL.yml): metadata and references
- Evidence: raw artifacts (events.json, tree.json, RUNLOG.md)

## Roles

### Observer
The entity that runs a validation session and captures protocol communication. Typically uses proofscan as the observation tool.

### Notary
The service that timestamps and anchors evidence to immutable storage. Uses IPFS for content addressing and Hedera HCS for timestamping.

### Validator (Third-party)
An independent party that reproduces or reviews a validation session to provide external confirmation.

## Artifacts

### events.json
Raw JSON-RPC events captured during a session. The primary evidence of protocol communication.

### tree.json
Hierarchical structure of connectors, sessions, and RPC calls. Provides navigation context.

### RUNLOG.md
Human-readable execution log. Documents the session flow, commands executed, and observations.

### POPL.yml
The manifest file for a POPL entry. References artifacts, records metadata, and tracks trust levels.

## Trust Components

### Level
One of four trust tiers (0-3) indicating the degree of verification for an entry.

### Notarization
The process of anchoring evidence to IPFS (content) and Hedera HCS (time).

### Attribution
Linking a validation session to a verifiable identity (DID + signature).

## Infrastructure

### proofscan
The observation tool that captures MCP/A2A protocol communication. Stores evidence in `validation/session-.../`.

### inscribe-mcp
The notarization tool that bundles evidence to IPFS and records hashes on Hedera HCS.

### POP@AI
The human-readable publication layer. Articles that reference POPL entries with Proof Badges.

## Formats

### Evidence Reference
A pointer from POPL.yml to artifact location:
```yaml
evidence:
  git:
    path: validation/session-2026-01-02-time/events.json
```

### Proof Badge
A copy-paste block for articles containing:
- Entry ID
- Git commit
- Artifacts list
- Notarization references (IPFS CID, HCS transaction)

### Content Hash
SHA-256 hash of an artifact, recorded in POPL.yml for integrity verification.
