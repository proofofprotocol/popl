# POPL Entry Specification v0.0

This document defines the structure of a POPL entry manifest (POPL.yml).

## Design Principles

1. **Manifest, not duplication**: POPL.yml references artifacts, does not copy their contents
2. **Human-readable**: YAML format, clear field names
3. **Minimal required fields**: Only what's necessary for Level 0+1
4. **Extensible**: Optional fields for Level 2+3

## Required vs Optional

| Field | Required | Level |
|-------|----------|-------|
| `popl.spec` | Yes | 0 |
| `entry_id` | Yes | 0 |
| `title` | Yes | 0 |
| `author` | Yes | 0 |
| `levels` | Yes | 0 |
| `observed` | Yes | 0 |
| `target` | Yes | 0 |
| `tooling` | Yes | 0 |
| `evidence.git` | Yes | 0 |
| `evidence.artifacts` | Yes | 0 |
| `notarization` | Yes | 1 |
| `attribution` | No | 2 |
| `validation.third_party` | No | 3 |

## Field Definitions

### popl

```yaml
popl:
  spec: popl-entry-v0.0
```

Declares the specification version this entry follows.

### entry_id

```yaml
entry_id: "popl-2026-01-02-time-001"
```

Unique identifier for this entry. Format: `popl-YYYY-MM-DD-<target>-<sequence>`

### title

```yaml
title: "MCP Server Time Validation (uvx ENOENT failure)"
```

Human-readable title describing the session.

### author

```yaml
author: "POP@AI Team"
```

Human-readable author name. Not a DID (that goes in attribution).

### levels

```yaml
levels:
  level_0_recorded: true
  level_1_notarized: true
  level_2_attributed: false
  level_3_third_party: false
```

Boolean flags indicating which trust levels are achieved.

### observed

```yaml
observed:
  timezone: "Asia/Tokyo"
  observed_at: "2026-01-02T21:48:00+09:00"
  environment: "Genspark Sandbox"
```

When and where the observation occurred.

### target

```yaml
target:
  protocol:
    name: "MCP"
    spec_version: "2024-11-05"
    source: "https://spec.modelcontextprotocol.io/specification/2024-11-05/"
  mcp_server:
    package: "@anthropic-ai/mcp-server-time"
    version: "latest"
    launch: "uvx mcp-server-time"
  evidence_ref: "events.json"
```

What was being validated. Includes protocol spec version and MCP server details.

### tooling

```yaml
tooling:
  observer:
    name: "proofscan"
    package: "@anthropic/proofscan"
    version: "0.9.0"
  notary:
    name: "inscribe-mcp"
    package: "@proofofprotocol/inscribe-mcp"
    version: "0.1.0"
```

Tools used for observation and notarization.

### evidence.git

```yaml
evidence:
  git:
    forge: "github"
    repo: "proofofprotocol/proofscan"
    commit: "abc123def456..."
    path: "validation/session-2026-01-02-time/"
```

Git location of evidence artifacts.

### evidence.artifacts

```yaml
evidence:
  artifacts:
    - name: "events.json"
      sha256: "abc123..."
    - name: "tree.json"
      sha256: "def456..."
    - name: "RUNLOG.md"
      sha256: "789ghi..."
```

List of artifacts with content hashes for integrity verification.

### notarization

```yaml
notarization:
  ipfs:
    bundle_cid: "bafybei..."
  hcs:
    topic_id: "0.0.7503789"
    transaction_id: "0.0.7503789-1234567890.123456789"
    payload_ref: "ipfs://bafybei..."
```

IPFS and Hedera HCS references for timestamping.

### attribution (Optional - Level 2)

```yaml
attribution:
  did: "did:key:z6Mk..."
  signature: "base64-encoded-signature"
  signed_hash: "sha256-of-evidence-bundle"
```

Cryptographic attribution to a verifiable identity.

### validation.third_party (Optional - Level 3)

```yaml
validation:
  third_party:
    - validator: "Independent Reviewer"
      attestation_url: "https://..."
      date: "2026-01-15"
```

External validation references.

## What Belongs Where

| Information | Location | Why |
|-------------|----------|-----|
| Metadata, references | POPL.yml | Structured, searchable |
| Raw events | events.json | Primary evidence |
| Session flow | RUNLOG.md | Human context |
| Tree structure | tree.json | Navigation |
| Full request/response bodies | events.json | Not duplicated in POPL.yml |

## Example POPL.yml

See [templates/POPL.yml](../templates/POPL.yml) for a complete template.
