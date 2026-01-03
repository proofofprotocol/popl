# POPL Trust Levels

POPL defines four trust levels for validation evidence. Each level answers a specific question about the recorded session.

## Level Overview

| Level | Name | Question Answered | Required |
|-------|------|-------------------|----------|
| 0 | Recorded | "What happened?" | **Yes** |
| 1 | Notarized | "When did it happen?" | **Yes** |
| 2 | Attributed | "Who observed it?" | No |
| 3 | Third-party | "Can someone else confirm?" | No |

## Level 0: Recorded

**Question:** What happened?

**Requirements:**
- Git commit containing evidence artifacts
- Artifacts: `events.json`, `tree.json`, `RUNLOG.md`
- POPL.yml manifest referencing artifacts

**Proves:**
- A validation session was captured
- Raw protocol data exists
- Artifacts are version-controlled

## Level 1: Notarized

**Question:** When did it happen?

**Requirements:**
- IPFS bundle with CID
- Hedera HCS message with timestamp
- Hash chain linking artifacts to HCS transaction

**Proves:**
- Evidence existed at a specific time
- Artifacts have not been modified since notarization
- Timestamp is from a decentralized, tamper-proof source

## Level 2: Attributed (Optional)

**Question:** Who observed it?

**Requirements:**
- DID (Decentralized Identifier) of observer
- Cryptographic signature over evidence hash
- Verifiable credential (optional)

**Proves:**
- A specific identity vouches for the observation
- The observer has a persistent, verifiable identity

## Level 3: Third-party (Optional)

**Question:** Can someone else confirm?

**Requirements:**
- Independent reproduction of the session
- Third-party attestation or review
- Cross-reference to external validation

**Proves:**
- The observation is reproducible
- Multiple parties agree on the evidence
- Higher confidence in accuracy

## Minimum Requirements for POPL Entry

A valid POPL entry **must** achieve:
- **Level 0** (Recorded): Git commit with artifacts
- **Level 1** (Notarized): IPFS + Hedera timestamp

Levels 2 and 3 are optional enhancements for higher trust scenarios.

## Implementation

```yaml
# In POPL.yml
levels:
  level_0_recorded: true      # Required
  level_1_notarized: true     # Required
  level_2_attributed: false   # Optional
  level_3_third_party: false  # Optional
```
