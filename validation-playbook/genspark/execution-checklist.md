# Genspark Execution Checklist

Copy-paste checklist for a single validation session.

---

## Pre-Session

- [ ] Sandbox launched
- [ ] Target MCP server identified: `________________`
- [ ] GitHub PAT ready

## Setup

- [ ] `git clone https://github.com/proofofprotocol/proofscan.git`
- [ ] `cd proofscan`
- [ ] `git config user.email` and `user.name` set
- [ ] `npm install -g .` or `npm link`
- [ ] `pfscan connectors add <target> --from-mcp-json '...'`
- [ ] `pfscan connectors list` shows target

## Execution

- [ ] `pfscan scan start <target>`
- [ ] `pfscan shell` entered
- [ ] `tool ls` executed
- [ ] Tool calls made and responses captured
- [ ] Session noted in RUNLOG.md

## Export

- [ ] Session directory created: `validation/session-YYYY-MM-DD-<target>/`
- [ ] `events.json` exported
- [ ] `tree.json` exported
- [ ] `RUNLOG.md` written

## POPL Entry

- [ ] `POPL.yml` created from template
- [ ] `entry_id` set: `________________`
- [ ] `observed_at` set: `________________`
- [ ] `target` details filled
- [ ] Hashes calculated: `sha256sum events.json tree.json RUNLOG.md`
- [ ] Hashes added to POPL.yml

## Commit

- [ ] `git add validation/session-.../`
- [ ] `git commit -m "validation: add session <target> (YYYY-MM-DD)"`
- [ ] `git push origin main`
- [ ] Commit SHA recorded: `________________`

## Notarize (Optional - Level 1)

- [ ] `inscribe @last` executed
- [ ] IPFS CID recorded: `________________`
- [ ] HCS transaction recorded: `________________`
- [ ] POPL.yml updated with notarization
- [ ] `git add POPL.yml && git commit --amend` or new commit
- [ ] `git push origin main`

## Post-Session

- [ ] Verify commit visible on GitHub
- [ ] Sandbox can be terminated
- [ ] Entry ID noted for POP@AI article

---

## Quick Reference

```bash
# Session directory
mkdir -p validation/session-$(date +%Y-%m-%d)-<target>

# Hashes
sha256sum events.json tree.json RUNLOG.md

# Commit
git add validation/session-*/
git commit -m "validation: add session <target> ($(date +%Y-%m-%d))"
git push origin main
```

---

## Failure Case

If the session fails (e.g., ENOENT, connection error):

- [ ] Still create session directory
- [ ] Export partial events.json (may be empty)
- [ ] Document error in RUNLOG.md
- [ ] Set title to include failure reason
- [ ] Commit as evidence (failures are valid observations)
