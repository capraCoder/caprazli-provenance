# Architecture: T-003 Dual-Layer Provenance Principle

## Statement

Independent researchers lacking institutional social proof require **dual-layer provenance**:

| Layer | Purpose | Timing |
|-------|---------|--------|
| **Continuous** | Cryptographic timestamping of daily work | Ongoing |
| **Formal** | Institutional registration (DOI) | At publication |

## Rationale

Traditional academia establishes priority through **social proof**:
- Colleagues who witnessed your work
- Lab notebooks countersigned by supervisors
- Seminar presentations with dated records
- Peer review timestamps

Independent researchers lack this infrastructure. **Cryptographic proof** substitutes for social proof:
- Blockchain timestamps are mathematical, not social
- Verification requires no institutional access
- Proofs persist as long as the blockchain exists

## Historical Precedent

| Era | Priority Method |
|-----|-----------------|
| 1600s | Anagrams (Galileo, Huygens) |
| 1670s | Sealed letters (Newton vs Leibniz) |
| 1850s | Rush to publish (Darwin) |
| 1900s | Witnessed lab notebooks |
| 2020s | Blockchain timestamping |

Each era's solution substitutes a more fundamental mechanism for social trust.

## Implementation: A-003

### Components

| Component | Role | Trust Model |
|-----------|------|-------------|
| Git + GPG signing | Local hash chain with identity | Your key |
| OpenTimestamps | Bitcoin blockchain anchor | Bitcoin network |
| Zenodo | DOI registration | CERN/EU infrastructure |

### Workflow

```
Daily Work
    │
    ▼
Git commit (optionally signed)
    │
    ▼
OpenTimestamps stamp → .ots file (Bitcoin anchor)
    │
    │ When ready for publication
    ▼
Zenodo upload → DOI (formal registration)
```

### Properties

- **Continuous:** Daily work is timestamped
- **Immutable:** Bitcoin blockchain is most battle-tested ledger
- **Verifiable:** Anyone can verify .ots proofs decades later
- **Formal:** DOI provides academic recognition
- **Free:** No cost for any component
- **Trustless:** No company, no institution, no single point of failure

## Verification

To verify a timestamp:

```bash
ots verify file.pdf.ots
```

The .ots file contains:
1. Hash of the original file
2. Merkle path to Bitcoin block
3. Block height and timestamp

Anyone with the original file and .ots proof can verify independently.

## Theoretical Foundation

This implementation instantiates the Dual-Layer Provenance Principle (T-003) from the Caprazli methodological framework. The principle states that independent researchers require two complementary provenance layers to establish priority without institutional backing.

For the full theoretical framework, see:
- DOI: [10.5281/zenodo.18115235](https://doi.org/10.5281/zenodo.18115235)
