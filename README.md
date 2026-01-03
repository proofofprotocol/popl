# POPL: Proof of Protocol Ledger

> **Languages:** English | [日本語](README.ja.md)

**POPL** is the structured ledger format for recording AI protocol validation sessions. It answers: *What was observed? When? By whom? Can it be verified?*

## Philosophy

- **Proof of Protocol** = The philosophy of observable, verifiable AI communication
- **POPL** = The ledger structure that makes it permanent
- **POPL Entry** = One validation session, one record

## Repository Structure

```
popl/
├── SPEC/                    # Specification documents
│   ├── popl-entry-v0.0.md   # Entry format definition
│   ├── levels.md            # Trust levels (0-3)
│   └── terminology.md       # Glossary
├── templates/               # Ready-to-use templates
│   ├── POPL.yml             # Entry manifest template
│   └── EvidenceBlock.md     # Blog/article badge template
├── validation-playbook/     # How to run validation sessions
│   ├── principles.md        # Core principles
│   ├── genspark/            # Genspark sandbox instructions
│   └── local/               # Local execution policies
└── VERSIONING.md            # Version history
```

## Quick Start

1. **Run a validation session** using [proofscan](https://github.com/proofofprotocol/proofscan)
2. **Capture artifacts**: `events.json`, `tree.json`, `RUNLOG.md`
3. **Create POPL.yml** using [templates/POPL.yml](templates/POPL.yml)
4. **Commit to proofscan** under `validation/session-YYYY-MM-DD-<target>/`
5. **Notarize** (optional): IPFS + Hedera HCS via [inscribe-mcp](https://github.com/inscribepop/inscribe-mcp)

## Where Evidence Lives

| What | Where |
|------|-------|
| Spec, templates, playbooks | This repo (`popl`) |
| Evidence artifacts | [proofscan/validation/](https://github.com/proofofprotocol/proofscan/tree/main/validation) |
| Human-readable articles | [POP@AI](https://note.com/pop_ai/) |
| Notarization layer | [inscribe-mcp](https://github.com/inscribepop/inscribe-mcp) |

## Trust Levels

| Level | Name | What it proves | Required |
|-------|------|----------------|----------|
| 0 | Recorded | Git commit exists | Yes |
| 1 | Notarized | IPFS + Hedera timestamp | Yes |
| 2 | Attributed | DID/signature attached | No |
| 3 | Third-party | External validation | No |

See [SPEC/levels.md](SPEC/levels.md) for details.

## Key Links

- [SPEC/popl-entry-v0.0.md](SPEC/popl-entry-v0.0.md) - Entry format specification
- [templates/POPL.yml](templates/POPL.yml) - Ready-to-use template
- [validation-playbook/genspark/sandbox-instructions.md](validation-playbook/genspark/sandbox-instructions.md) - Genspark execution guide

## License

MIT
