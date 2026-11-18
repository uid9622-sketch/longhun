<!--
DNA: #龍芯⚡️2026-11-18-BEHAVIORAL-CRYPTOGRAPHY-FULL-PAPER-v1.0
GPG: A2D0092CEE2E5BA87035600924C3704A8CC26D5F
CONFIRM: #CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z
SEAL: #ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL
License: CC BY-NC-SA 4.0 + Longhun DNA Inheritance Clause
Part of: Behavioral Cryptography Full Paper v1.0 (see README.md)
-->

## 3.5 Evidence Ledger and Lineage Chain

### 3.5.1 Motivation

The Dynamic DNA Engine introduced in Section 3.4 creates a compact provenance root for individual artifacts or actions. However, provenance does not emerge from isolated identifiers. It emerges from continuity.

A single DNA record can show that one artifact was generated under a specific identity, time, module, and action. But content creation in human-AI collaboration is rarely a single-step process. It usually involves multiple revisions, model interactions, rule applications, persona routing decisions, corrections, mistakes, and re-exports.

Therefore, Behavioral Cryptography requires an append-only evidence ledger that records each significant action and links it to previous actions.

The central principle is:

A single DNA proves a point.

A ledger proves a path.

A lineage chain proves continuity.

In Chinese:

一个 DNA 是点；证据账本是线；血统链是路。


---


### 3.5.2 Ledger Design Goals

The Evidence Ledger is designed around eight goals.

G1. Append-Only Recording

The ledger must not silently overwrite past records.

Every correction, update, deletion request, export, or re-signing action should produce a new entry.

append_only_principle:

```python
- append_new_entry
- mark_previous_entry_superseded
- add_correction_record
- add_revocation_record
```

```python
- silent_overwrite
- delete_without_tombstone
- rewrite_history_without_notice
```

G2. Parent-Child Lineage

Every derived artifact should preserve a parent DNA reference.

lineage_rule:

root_artifact:

```python
parent_dna: null
```

derived_artifact:

```python
parent_dna: required
```

exported_artifact:

```python
parent_dna: required
```

summarized_artifact:

```python
parent_dna: required
```

corrected_artifact:

```python
parent_dna: previous_version_dna
```

G3. Hash-Linked Integrity

Each ledger entry includes the hash of the previous ledger entry. This creates a local hash chain.

h_0 = SHA256(entry_0)

h_1 = SHA256(h_0 || entry_1)

h_2 = SHA256(h_1 || entry_2)

...

h_n = SHA256(h_{n-1} || entry_n)

If any entry is changed, all subsequent hashes become invalid.

G4. Human-Auditable Evidence

The ledger must be inspectable by a non-enterprise user.

This matters because Behavioral Cryptography is designed for civilian-grade provenance, not only institutional compliance.

human_auditability:

format: jsonl

readable_fields:

```python
- event
- dna
- parent_dna
- action
- module
- timestamp
- audit_color
- reason
```

G5. Privacy-Aware Storage

The ledger must not become a privacy leak.

For sealed or burn content, the ledger should record only metadata and hash.

privacy_ledger_policy:

normal:

```python
may_store_summary: true
may_store_artifact_hash: true
```

burn:

```python
may_store_raw_content: false
may_store_summary: false
must_store_destroy_proof: true
```

sealed:

```python
may_store_raw_content: false
may_store_summary: false
must_store_hash_only: true
```

G6. Multi-Factor Linkage

The ledger must connect to the seven-factor framework.

ledger_links:

F1_identity_dna: dna / uid / gpg_prefix

F2_temporal_anchor: iso_time / shichen / digit_root

F3_rule_trace: rule_id / rule_dna / rule_version

F4_persona_route: persona_id / persona_dna

F5_protected_lexicon: lexicon_version_hash

F6_style_vector: style_baseline_hash

F7_mistake_ledger: mistake_entry_id / correction_dna

G7. Revocation and Correction

A provenance system must allow correction without erasing history.

correction_policy:

wrong_entry:

```python
do_not_delete: true
append_correction: true
link_to_original: true
```

revoked_entry:

```python
append_revocation_record: true
preserve_original_hash: true
```

G8. Exportable Proof Bundle

The ledger should support export as a proof bundle.

proof_bundle:

includes:

```python
- artifact
- dynamic_dna_record
- relevant_ledger_entries
- public_key_or_gpg_fingerprint
- hash_chain_proof
- optional_signature
```


---


### 3.5.3 Ledger Entry Model

Each ledger entry is a structured record.

Canonical Ledger Entry

{

"ledger_version": "v1.0",

"entry_id": "LEDGER-9622-20260504-000001",

"event": "ARTIFACT_CREATED",

"dna": "#龍芯⚡️2026-05-04-午时-金-BEHAVIORAL-VERIFY-A2D0092C-7FA3C91B",

"parent_dna": "#龍芯⚡️2026-05-04-BEHAVIORAL-CRYPTOGRAPHY-DYNAMIC-DNA-ENGINE-v1.0",

"child_dna": null,

"uid": "UID9622",

"module": "BEHAVIORAL-VERIFY",

"action": "CREATE_SECTION",

"artifact_hash": "sha256:7fa3c91b84d5...",

"privacy_mode": "normal",

"retention": "full",

"trace_mode": "chain",

"audit_color": "🟢",

"reason": "Section 3.5 evidence ledger entry generated.",

"iso_time": "2026-05-04T12:40:00+08:00",

"previous_entry_hash": "sha256:...",

"current_entry_hash": "sha256:...",

"confirm": "#CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z",

"seal": "#ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL"

}


---


### 3.5.4 Ledger Event Types

The ledger should distinguish event types clearly.

ledger_events:

creation:

```python
- ARTIFACT_CREATED
- DNA_GENERATED
- RULE_APPLIED
- PERSONA_DISPATCHED
```

revision:

```python
- ARTIFACT_REVISED
- SUMMARY_CREATED
- TRANSLATION_CREATED
- FORMAT_CONVERTED
```

audit:

```python
- AUDIT_PASSED
- AUDIT_PENDING
- AUDIT_FAILED
- HARD_FAILURE_TRIGGERED
```

privacy:

```python
- BURN_PROCESSED
- DESTROY_PROOF_CREATED
- SEALED_HASH_ONLY
- NO_EXTERNAL_BLOCKED
```

correction:

```python
- MISTAKE_RECORDED
- CORRECTION_APPENDED
- ENTRY_REVOKED
```

export:

```python
- EXPORT_REQUESTED
- EXPORT_APPROVED
- EXPORT_BLOCKED
- PROOF_BUNDLE_CREATED
```


---


### 3.5.5 Lineage Chain Definition

Definition 3.5 — Evidence Ledger

An evidence ledger L is an ordered sequence of entries:

L = langle e_1, e_2, ..., e_n rangle

where each entry e_i contains:

e_i = langle dna_i, parent_i, action_i, time_i, hash_i, prevhash_i, audit_i rangle

Definition 3.6 — Lineage Chain

A lineage chain for artifact C_n is the ordered path:

Chain(C_n) = langle dna_0 rightarrow dna_1 rightarrow ... rightarrow dna_n rangle

where each dna_i is either the parent of dna_{i+1}, or is referenced through a valid ledger entry.

Definition 3.7 — Chain Continuity

A chain is continuous if:

1. Every non-root node has a valid parent_dna.
2. Every parent_dna exists in the ledger or in an accepted external checkpoint.
3. Timestamps are monotonic or explainably branched.
4. The ledger hash chain verifies.
5. No sealed or no_external record is exported without authorization.


---


### 3.5.6 Algorithm 4: Append Ledger Entry

from**future**import annotations

import hashlib

import json

from dataclasses import dataclass, asdict

from datetime import datetime, timezone

from pathlib import Path

from typing import Optional, Literal

AuditColor = Literal["🟢", "🟡", "🔴"]

PrivacyMode = Literal["normal", "burn", "sealed"]

RetentionMode = Literal["full", "summary_only", "hash_only"]

TraceMode = Literal["chain", "local_only", "no_external"]

@dataclass

class LedgerEntry:

```python
ledger_version: str
entry_id: str
event: str
dna: str
parent_dna: Optional[str]
child_dna: Optional[str]
uid: str
module: str
action: str
artifact_hash: str
privacy_mode: PrivacyMode
retention: RetentionMode
trace_mode: TraceMode
audit_color: AuditColor
reason: str
iso_time: str
previous_entry_hash: str
current_entry_hash: str
confirm: str
seal: str
```

def now_iso() -> str:

```python
return datetime.now(timezone.utc).astimezone().isoformat(timespec="seconds")
```

def canonical_json(data: dict) -> str:

```python
return json.dumps(data, ensure_ascii=False, sort_keys=True, separators=(",", ":"))
```

def sha256_string(text: str) -> str:

```python
return "sha256:" + hashlib.sha256(text.encode("utf-8")).hexdigest()
```

def load_last_hash(ledger_path: Path) -> str:

```python
if not ledger_path.exists():
    return "sha256:GENESIS"
last_line = ""
with ledger_path.open("r", encoding="utf-8") as f:
    for line in f:
        if line.strip():
            last_line = line.strip()
if not last_line:
    return "sha256:GENESIS"
try:
    last_entry = json.loads(last_line)
    return last_entry.get("current_entry_hash", "sha256:GENESIS")
except Exception:
    return "sha256:CORRUPTED"
```

def compute_entry_hash(entry_without_current_hash: dict) -> str:

```python
canonical = canonical_json(entry_without_current_hash)
return sha256_string(canonical)
```

def append_ledger_entry(

```python
ledger_path: Path,
event: str,
dna: str,
parent_dna: Optional[str],
uid: str,
module: str,
action: str,
artifact_hash: str,
privacy_mode: PrivacyMode,
retention: RetentionMode,
trace_mode: TraceMode,
audit_color: AuditColor,
reason: str,
child_dna: Optional[str] = None,
confirm: str = "#CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z",
seal: str = "#ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL",
```

) -> LedgerEntry:

```python
ledger_path.parent.mkdir(parents=True, exist_ok=True)
previous_hash = load_last_hash(ledger_path)
ts = now_iso()
# Basic privacy safety checks.
if privacy_mode == "sealed" and retention != "hash_only":
    raise ValueError("sealed content must use hash_only retention")
if privacy_mode == "burn" and retention == "full":
    raise ValueError("burn content must not use full retention")
if trace_mode == "no_external" and event.startswith("EXPORT"):
    raise ValueError("no_external content cannot be exported")
entry_id_seed = f"{ts}|{dna}|{event}|{previous_hash}"
entry_id = "LEDGER-9622-" + hashlib.sha256(entry_id_seed.encode()).hexdigest()[:12].upper()
base = {
    "ledger_version": "v1.0",
    "entry_id": entry_id,
    "event": event,
    "dna": dna,
    "parent_dna": parent_dna,
# ... (11 行代码省略) ...
    "previous_entry_hash": previous_hash,
    "confirm": confirm,
    "seal": seal
}
current_hash = compute_entry_hash(base)
base["current_entry_hash"] = current_hash
entry = LedgerEntry(**base)
with ledger_path.open("a", encoding="utf-8") as f:
    f.write(json.dumps(asdict(entry), ensure_ascii=False) + "\n")
return entry
```


---


### 3.5.7 Algorithm 5: Verify Ledger Integrity

def verify_ledger_integrity(ledger_path: Path) -> tuple[bool, list[str]]:

```python
evidence = []
if not ledger_path.exists():
    return False, ["Ledger file does not exist"]
previous_hash = "sha256:GENESIS"
line_no = 0
with ledger_path.open("r", encoding="utf-8") as f:
    for line in f:
        line_no += 1
        if not line.strip():
            continue
        try:
            entry = json.loads(line)
        except json.JSONDecodeError:
            return False, [f"Line {line_no}: invalid JSON"]
        recorded_previous = entry.get("previous_entry_hash")
        recorded_current = entry.get("current_entry_hash")
        if recorded_previous != previous_hash:
            return False, [
                f"Line {line_no}: previous hash mismatch",
                f"expected={previous_hash}",
                f"actual={recorded_previous}"
            ]
        entry_without_current = dict(entry)
        entry_without_current.pop("current_entry_hash", None)
        recomputed = compute_entry_hash(entry_without_current)
        if recomputed != recorded_current:
            return False, [
                f"Line {line_no}: current hash mismatch",
                f"expected={recomputed}",
                f"actual={recorded_current}"
            ]
        previous_hash = recorded_current
        evidence.append(f"Line {line_no}: verified {entry.get('entry_id')}")
return True, evidence
```


---


### 3.5.8 Algorithm 6: Verify Lineage Chain

def build_dna_index(ledger_path: Path) -> dict[str, dict]:

```python
index = {}
if not ledger_path.exists():
    return index
with ledger_path.open("r", encoding="utf-8") as f:
    for line in f:
        if not line.strip():
            continue
        entry = json.loads(line)
        dna = entry.get("dna")
        if dna:
            index[dna] = entry
return index
```

def verify_lineage_chain(

```python
ledger_path: Path,
target_dna: str,
allow_external_roots: bool = True
```

) -> tuple[bool, list[str]]:

```python
index = build_dna_index(ledger_path)
evidence = []
if target_dna not in index:
    return False, [f"Target DNA not found: {target_dna}"]
seen = set()
current = target_dna
while current:
    if current in seen:
        return False, [f"Cycle detected at {current}"]
    seen.add(current)
    entry = index.get(current)
    if not entry:
        if allow_external_roots:
            evidence.append(f"External root accepted: {current}")
            break
        return False, [f"Missing parent DNA: {current}"]
    evidence.append(f"DNA found: {current}")
    # Privacy rule check
    if entry.get("privacy_mode") == "sealed" and entry.get("retention") != "hash_only":
        return False, [f"Sealed record violates hash_only retention: {current}"]
    if entry.get("trace_mode") == "no_external" and entry.get("event", "").startswith("EXPORT"):
        return False, [f"no_external record exported illegally: {current}"]
    parent = entry.get("parent_dna")
    if not parent:
        evidence.append("Root reached")
        break
    current = parent
return True, evidence
```


---


### 3.5.9 Correction, Revocation, and Mistake Ledger Integration

Behavioral Cryptography does not assume that creators never make mistakes. Instead, it treats honest correction as evidence.

This is where Mistake Ledger becomes important.

Correction Entry

{

"event": "CORRECTION_APPENDED",

"dna": "#龍芯⚡️2026-05-04-酉时-金-CORRECTION-A2D0092C-89AB12CD",

"parent_dna": "#龍芯⚡️2026-05-04-午时-金-BEHAVIORAL-VERIFY-A2D0092C-7FA3C91B",

"mistake_id": "MISTAKE-9622-20260504-001",

"reason": "Corrected an overclaim about cryptographic unforgeability.",

"correction_type": "CLAIM_DOWNGRADE",

"audit_color": "🟢",

"retention": "summary_only"

}

Revocation Entry

{

"event": "ENTRY_REVOKED",

"dna": "#龍芯⚡️2026-05-04-戌时-金-REVOCATION-A2D0092C-EF9012AB",

"parent_dna": "#龍芯⚡️2026-05-04-午时-金-BEHAVIORAL-VERIFY-A2D0092C-7FA3C91B",

"revoked_dna": "#龍芯⚡️2026-05-04-午时-金-BEHAVIORAL-VERIFY-A2D0092C-7FA3C91B",

"reason": "Previous artifact was superseded by corrected version.",

"audit_color": "🟡",

"retention": "summary_only"

}

Why Mistakes Strengthen Provenance

Attackers often copy polished outputs. They rarely reproduce the full history of false starts, corrections, boundary clarifications, and mistakes.

Therefore:

A continuous mistake ledger is a behavioral authenticity signal.

真作者会留下修正痕迹；洗稿者只想留下完美成品。


---


### 3.5.10 Branching and Merge Semantics

Human-AI collaboration often branches.

Examples:

branch_examples:

- Claude produces formalization
- ChatGPT produces compression
- Cursor implements code
- Notion stores structured record
- GitHub exports public version

The lineage model must support branching.

DNA_ROOT

├── DNA_CLAUDE_DRAFT

├── DNA_CHATGPT_COMPRESSION

├── DNA_CURSOR_IMPLEMENTATION

└── DNA_PUBLIC_EXPORT

Merge Entry

{

"event": "LINEAGE_MERGED",

"dna": "#龍芯⚡️2026-05-04-未时-土-LINEAGE-MERGE-A2D0092C-3C4D5E6F",

"parent_dna": "#龍芯⚡️2026-05-04-BEHAVIORAL-CRYPTOGRAPHY-DYNAMIC-DNA-ENGINE-v1.0",

"merged_parents": [

```python
"#龍芯⚡️2026-05-04-CLAUDE-DRAFT-v1.0",
"#龍芯⚡️2026-05-04-CHATGPT-COMPRESSION-v1.0",
"#龍芯⚡️2026-05-04-CURSOR-IMPLEMENTATION-v1.0"
```

],

"action": "MERGE_BRANCHES",

"reason": "Merged multi-AI outputs into UID9622 canonical version.",

"audit_color": "🟢"

}

Hard rule:

Merge does not erase parents. Merge records them.


---


### 3.5.11 Security Properties (Stated as Propositions)

Proposition 3.10 — Ledger Tamper Evidence

If any ledger entry e_i is modified after creation, then the hash verification for e_i or some later entry e_j fails.

Proof Sketch.

Each entry stores previous_entry_hash and current_entry_hash. The current hash is computed over the canonical entry content. Modifying an entry changes its computed hash. Since the next entry stores the previous hash, the mismatch propagates. ∎

Proposition 3.11 — Lineage Continuity

If every derived artifact contains a valid parent_dna, and every parent exists in the ledger or external checkpoint, then the artifact has a continuous lineage chain to a known root.

Proof Sketch.

Starting from the target DNA, repeatedly follow parent_dna. If each parent exists and no cycle appears, the chain terminates at a root or accepted checkpoint. ∎

Proposition 3.12 — Correction Preservation

Appending correction records preserves accountability better than overwriting prior records.

Proof Sketch.

Overwriting removes evidence of the previous state. Appending creates a new record that references the earlier record. The prior claim, the correction, and the reason remain available for audit. ∎

Proposition 3.13 — No Silent Laundering

If a content artifact is paraphrased or exported without a valid parent DNA, the ledger verification fails to establish continuous lineage.

Proof Sketch.

The exported artifact may have its own hash and DNA, but without a valid parent_dna chain, it cannot prove descent from the original source. ∎


---


### 3.5.12 Privacy and Boundary Enforcement

The ledger enforces privacy rules.

Boundary Table

Mode Raw Content Summary Hash Export

normal Allowed by retention Allowed Required Allowed if trace permits

burn Temporary only No Required Usually blocked

sealed Never No Required Blocked

no_external Local only Local only Local only Blocked

One-Line Rule

The ledger records proof of handling; it does not justify storing what should not be stored.

**中文注：**

账本只证明处理过，不代表可以把敏感原文留下来。


---


### 3.5.13 Reviewer Defense Paragraph

This section should include a clear academic defense to prevent overclaiming.


The proposed ledger is not claimed to be equivalent to a public blockchain or a trusted timestamping authority. In its minimal deployment, it provides local tamper-evident continuity rather than global immutability. Stronger guarantees can be obtained by periodically anchoring ledger heads to external systems such as Git commits, public archives, timestamping services, or institutional repositories. This layered design is intentional: it allows civilian users to obtain meaningful provenance protection without requiring enterprise infrastructure.

本地账本不是区块链，不吹全球不可改；它先做到本地防篡改、有痕迹、能验证。要更强，就定期把账本头 hash 发到 Git / 公开仓库 / 时间戳服务做外锚。


---


### 3.5.14 Transition to Section 3.6