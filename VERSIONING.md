# POPL Versioning

## Current Version

**POPL Spec: v0.0** (Initial draft)

## Version History

| Version | Date | Changes |
|---------|------|---------|
| v0.0 | 2026-01-02 | Initial spec, templates, and playbook |

## Versioning Policy

### Spec Versions

POPL entry spec versions follow semantic versioning:

- **Major (v1.0)**: Breaking changes to required fields
- **Minor (v0.1)**: New optional fields, backward compatible
- **Patch (v0.0.1)**: Clarifications, typo fixes

### Backward Compatibility

- New spec versions should be able to read old entries
- Old parsers may not understand new optional fields
- Breaking changes require major version bump

### POPL.yml Declaration

Each entry declares its spec version:

```yaml
popl:
  spec: popl-entry-v0.0
```

### Migration

When updating to a new spec version:

1. Update `popl.spec` field
2. Add any new required fields
3. Validate against new spec
4. Re-commit (no need to re-notarize unless content changed)

## Roadmap

### v0.1 (Planned)

- Batch entry support
- Protocol version detection automation
- Tooling version auto-detection

### v1.0 (Future)

- Stable field definitions
- Schema validation tooling
- Official JSON Schema

## Contributing

Spec changes should be proposed via GitHub issues before implementation.
