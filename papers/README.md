# Papers

Each subdirectory is an independent research unit. The repository supplies shared
standards; it does not merge authorship, review status, versions, or evidence across
papers.

## Registered units

| Unit | Repository state | Notes |
|---|---|---|
| `AI_HALLUCINATION/` | Structure initialized | External v0.3 candidate is not imported. Experiments remain `NOT_RUN`. |
| `behavioral-cryptography/` | Existing manuscript retained | Original lowercase path and chapter files remain unchanged; review is `UNVERIFIED`. |
| `WEB3_DNA/` | Structure initialized | No manuscript or completed review is implied. |
| `AI_GOVERNANCE/` | Structure initialized | No manuscript or completed review is implied. |

The existing `behavioral-cryptography` path is intentionally preserved rather than
creating a duplicate uppercase directory or destructively migrating the manuscript.

## Per-paper layout

- `manuscripts/`: versioned drafts and immutable release snapshots.
- `formulas/`: formula source, symbol definitions, and checkable calculations.
- `literature/`: bibliographic records and claim-to-source mappings.
- `experiments/`: preregistration, inputs, code, outputs, and limitations.
- `reviews/`: append-only review reports with reviewer independence stated.
- `evidence/`: supporting evidence with provenance and integrity metadata.
- `releases/`: release metadata, hashes, tags, backups, and signatures when applicable.

See `registry/paper_registry.yaml` and `registry/version_registry.yaml` for recorded
state. A registry entry is not proof that an artifact or experiment exists.
