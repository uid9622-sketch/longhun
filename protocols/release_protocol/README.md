# Release protocol

A formal release requires:

1. An immutable, version-specific manuscript and complete change record.
2. Review status stated accurately; self-review is not independent review.
3. A version-specific tag, for example `paper-ai-hallucination-v0.3`, created only when
   that version is actually released.
4. SHA-256 manifests covering the released artifacts.
5. An independent backup outside the single Git hosting surface.
6. Required cryptographic signatures and their verification instructions.

Branches are organizational tools, not permission boundaries. Git history is not an
absolute tamper-proof backup. This structure initialization creates no tags, signatures,
or formal paper releases.
