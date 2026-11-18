<!--
DNA: #龍芯⚡️2026-11-18-BEHAVIORAL-CRYPTOGRAPHY-FULL-PAPER-v1.0
GPG: A2D0092CEE2E5BA87035600924C3704A8CC26D5F
CONFIRM: #CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z
SEAL: #ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL
License: CC BY-NC-SA 4.0 + Longhun DNA Inheritance Clause
Part of: Behavioral Cryptography Full Paper v1.0 (see README.md)
-->

## 3.4 The Dynamic DNA Engine

### 3.4.1 Motivation

The threat model in Section 3.3 shows that surface-level content can be copied, paraphrased, translated, and reformatted with minimal effort. A provenance framework therefore requires a lightweight mechanism that binds an artifact not only to a visible author name, but also to a structured generation context.

The Dynamic DNA Engine is designed for this purpose. It generates a human-readable, cryptographically anchored, and culturally meaningful provenance identifier for each significant artifact or action.

Unlike conventional content hashes, Dynamic DNA does not only summarize file content. It binds together:

dynamic_dna_inputs:

- creator identity
- claimed UID
- GPG fingerprint or public-key prefix
- timestamp
- cultural-temporal marker
- module name
- action type
- artifact digest
- audit route
- confirmation seal

This allows the resulting DNA string to serve as a compact entry point into the broader behavioral evidence chain.

The key design principle is:

A content hash proves that some bytes existed.

Dynamic DNA records who claimed the artifact, when, through which module, under which action, and under which audit route.


---


### 3.4.2 Design Goals

The Dynamic DNA Engine has seven design goals.

G1. Human-Readable Provenance

The identifier should be readable by ordinary users, not only by machines.

A conventional SHA-256 hash is technically useful but cognitively opaque. Dynamic DNA keeps the hash but wraps it inside a structured, human-readable format.

Example:

**龍芯⚡️2026-05-04-午时-金-BEHAVIORAL-VERIFY-A2D0092C-7FA3C91B**

This tells the user:

example_fields:

system: 龍芯

date: 2026-05-04

temporal_marker: 午时

element: 金

module: BEHAVIORAL-VERIFY

gpg_prefix: A2D0092C

hash8: 7FA3C91B

G2. Lightweight Civilian Deployment

The engine must run locally, without enterprise infrastructure.

Requirements:

civilian_deployability:

- no mandatory cloud service
- no enterprise PKI dependency
- no centralized institution required
- compatible with local JSONL logs
- compatible with Git commits
- compatible with Notion-style databases
- compatible with Markdown metadata blocks

G3. Cryptographic Anchoring

The DNA string must include or reference cryptographic evidence.

At minimum:

cryptographic_anchors:

- artifact_hash
- gpg_fingerprint_or_prefix
- timestamp
- signed_log_entry_optional

The system should not claim that a DNA string alone replaces a real digital signature. The correct framing is:

Dynamic DNA is a readable provenance identifier.

GPG or equivalent signatures provide cryptographic verification.

G4. Cultural-Temporal Embedding

The engine supports cultural-temporal markers such as shichen, wuxing, and digit root.

These markers are not treated as mystical security primitives. They serve three practical functions:

cultural_temporal_roles:

Academic phrasing:

Cultural-temporal markers act as human-interpretable consistency metadata rather than standalone cryptographic proofs.

UID9622 说法：

不是靠五行防伪，是靠五行让系统认路；真正防伪靠 hash、签名、日志和链路一致性。

G5. Append-Only Compatibility

Every generated DNA should be suitable for append-only ledgers.

Supported storage targets:

storage_targets:

- local_jsonl
- sqlite
- git_commit_log
- markdown_frontmatter
- notion_database
- signed_snapshot
- public_checkpoint

G6. Privacy-Safe Metadata

The engine must not force private content into visible DNA strings.

Sensitive content should be represented through hashes and metadata only.

Policy:

privacy_policy:

normal:

```python
may_include: ["module", "action", "date", "hash_prefix"]
```

burn:

```python
may_include: ["hash", "timestamp", "destroy_proof"]
must_not_include: ["raw_private_content"]
```

sealed:

```python
may_include: ["hash", "sealed_status", "timestamp"]
must_not_include: ["raw_content", "semantic_summary"]
```

G7. Verification-Oriented Output

Every DNA output should be parseable by the verification system.

It must support:

- parse_identity
- parse_timestamp
- parse_module
- parse_action
- parse_gpg_prefix
- parse_hash
- compare_with_audit_log
- compare_with_artifact_digest


---


### 3.4.3 DNA Data Model

A Dynamic DNA record is a structured object. The visible DNA string is only one projection of the full record.

Canonical Record

{

"dna": "#龍芯⚡️2026-05-04-午时-金-BEHAVIORAL-VERIFY-A2D0092C-7FA3C91B",

"uid": "UID9622",

"creator": "Zhuge Xin",

"gpg_fingerprint": "A2D0092CEE2E5BA87035600924C3704A8CC26D5F",

"gpg_prefix": "A2D0092C",

"iso_time": "2026-05-04T12:30:00+08:00",

"date": "2026-05-04",

"shichen": "午时",

"digit_root": 4,

"wuxing": "金",

"module": "BEHAVIORAL-VERIFY",

"action": "CREATE_SECTION",

"artifact_hash": "sha256:7fa3c91b84d5...",

"hash8": "7FA3C91B",

"privacy_mode": "normal",

"retention": "full",

"trace_mode": "chain",

"audit_color": "🟢",

"parent_dna": "#龍芯⚡️2026-05-04-BEHAVIORAL-CRYPTOGRAPHY-THREAT-MODEL-v1.0",

"confirm": "#CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z",

"seal": "#ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL"

}

Canonical Field Table

Field Purpose Required

dna Human-readable provenance identifier Yes

uid Claimed UID or originator identity Yes

gpg_fingerprint Cryptographic identity anchor Recommended

iso_time Machine-readable time Yes

shichen Human-readable cultural time marker Optional but used in Longhun

digit_root Routing checksum / semantic classification Optional

wuxing Semantic routing category Optional

module Source module or subsystem Yes

action What happened Yes

artifact_hash Digest of artifact or payload Yes

privacy_mode normal / burn / sealed Yes

retention full / summary_only / hash_only Yes

trace_mode chain / local_only / no_external Yes

parent_dna Previous lineage anchor Recommended

confirm UID9622 confirmation marker System-specific

seal UID9622 sovereign seal System-specific


---


### 3.4.4 DNA String Format

The visible DNA string follows a compact pattern.

**龍芯⚡️{date}-{shichen}-{wuxing}-{module}-{gpg_prefix}-{hash8}**

Formal Grammar

DynamicDNA ::= Prefix Date "-" Shichen "-" Wuxing "-" Module "-" GPGPrefix "-" Hash8

Prefix ::= "#龍芯⚡️"

Date ::= YYYY "-" MM "-" DD

Shichen ::= "子时" | "丑时" | "寅时" | "卯时" | "辰时" | "巳时" |

```python
                "午时" | "未时" | "申时" | "酉时" | "戌时" | "亥时"
```

Wuxing ::= "金" | "木" | "水" | "火" | "土"

Module ::= UppercaseAlphaNumDash

GPGPrefix ::= Hex{8}

Hash8 ::= Hex{8}

Example

**龍芯⚡️2026-05-04-午时-金-BEHAVIORAL-VERIFY-A2D0092C-7FA3C91B**

Non-Canonical Short Form

For contexts where the full form is too long:

**龍芯⚡️2026-05-04-BEHAVIORAL-DNA-v1.0**

Short form is acceptable for human-facing documents but should be paired with a full JSON record when used for verification.


---


### 3.4.5 Cultural-Temporal Mapping

The engine supports a cultural-temporal layer.

This layer is not treated as a replacement for cryptographic proof. It is a semantic checksum and routing layer.

Shichen Mapping

SHICHEN = [

```python
"子时", "丑时", "寅时", "卯时",
"辰时", "巳时", "午时", "未时",
"申时", "酉时", "戌时", "亥时"
```

]

def calc_shichen(hour: int) -> str:

```python
"""
Traditional Chinese shichen.
子时 covers 23:00-00:59.
This simplified implementation maps local hour to a 2-hour block.
"""
idx = ((hour + 1) % 24) // 2
return SHICHEN[idx]
```

Digit Root

def digit_root_from_text(text: str) -> int:

```python
digits = [int(c) for c in str(text) if c.isdigit()]
if not digits:
    return 0
n = sum(digits)
while n >= 10:
    n = sum(int(c) for c in str(n))
return n
```

Wuxing Mapping

The Longhun implementation uses digit root to route artifacts into five semantic categories.

DR_TO_WUXING = {

```python
1: "水",
2: "火",
3: "木",
4: "金",
5: "土",
6: "水",
7: "火",
8: "木",
9: "金",
0: "土"
```

}

Audit Gate Mapping

def audit_color_from_digit_root(dr: int) -> str:

```python
if dr in {3, 9}:
    return "🔴"
if dr == 6:
    return "🟡"
return "🟢"
```

Academic boundary statement:

Digit root and wuxing mapping are used as deterministic semantic routing features, not as cryptographic primitives.


---


### 3.4.6 Core Algorithm

Algorithm 2: GenerateDynamicDNA

from**future**import annotations

import hashlib

import json

from dataclasses import dataclass, asdict

from datetime import datetime, timezone

from typing import Optional, Literal

PrivacyMode = Literal["normal", "burn", "sealed"]

RetentionMode = Literal["full", "summary_only", "hash_only"]

TraceMode = Literal["chain", "local_only", "no_external"]

SHICHEN = [

```python
"子时", "丑时", "寅时", "卯时",
"辰时", "巳时", "午时", "未时",
"申时", "酉时", "戌时", "亥时"
```

]

DR_TO_WUXING = {

```python
1: "水",
2: "火",
3: "木",
4: "金",
5: "土",
6: "水",
7: "火",
8: "木",
9: "金",
0: "土"
```

}

@dataclass

class DynamicDNARecord:

```python
dna: str
uid: str
creator: str
gpg_fingerprint: str
gpg_prefix: str
iso_time: str
date: str
shichen: str
digit_root: int
wuxing: str
module: str
action: str
artifact_hash: str
hash8: str
privacy_mode: PrivacyMode
retention: RetentionMode
trace_mode: TraceMode
audit_color: str
parent_dna: Optional[str]
confirm: str
seal: str
```

def calc_shichen(dt: datetime) -> str:

```python
hour = dt.hour
idx = ((hour + 1) % 24) // 2
return SHICHEN[idx]
```

def digit_root(text: str) -> int:

```python
digits = [int(c) for c in str(text) if c.isdigit()]
if not digits:
    return 0
n = sum(digits)
while n >= 10:
    n = sum(int(c) for c in str(n))
return n
```

def wuxing_from_dr(dr: int) -> str:

```python
return DR_TO_WUXING.get(dr, "土")
```

def audit_color_from_dr(dr: int) -> str:

```python
if dr in {3, 9}:
    return "🔴"
if dr == 6:
    return "🟡"
return "🟢"
```

def sha256_text(text: str) -> str:

```python
return hashlib.sha256(text.encode("utf-8", errors="ignore")).hexdigest()
```

def normalize_module(module: str) -> str:

```python
keep = []
for ch in module.upper().strip():
    if ch.isalnum() or ch in {"-", "_"}:
        keep.append(ch)
    elif ch.isspace():
        keep.append("-")
value = "".join(keep).strip("-")
return value[:40] if value else "UNNAMED-MODULE"
```

def generate_dynamic_dna(

```python
artifact: str,
module: str,
action: str,
uid: str = "UID9622",
creator: str = "Zhuge Xin",
gpg_fingerprint: str = "A2D0092CEE2E5BA87035600924C3704A8CC26D5F",
parent_dna: Optional[str] = None,
privacy_mode: PrivacyMode = "normal",
retention: RetentionMode = "full",
trace_mode: TraceMode = "chain",
confirm: str = "#CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z",
seal: str = "#ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL",
now: Optional[datetime] = None
```

) -> DynamicDNARecord:

```python
"""
Generate a dynamic provenance identifier for an artifact.
This function creates a human-readable DNA string and a structured
verification record. It does not replace GPG signing; rather, it
prepares a canonical record that may be signed or appended to a ledger.
"""
if now is None:
    now = datetime.now(timezone.utc).astimezone()
iso_time = now.isoformat(timespec="seconds")
date = now.strftime("%Y-%m-%d")
shichen = calc_shichen(now)
module_norm = normalize_module(module)
action_norm = normalize_module(action)
artifact_hash_full = sha256_text(artifact)
hash8 = artifact_hash_full[:8].upper()
# Seed includes human identity, time, module, action, artifact digest, and parent DNA.
seed = "|".join([
    uid,
# ... (27 行代码省略) ...
    artifact_hash=f"sha256:{artifact_hash_full}",
    hash8=hash8,
    privacy_mode=privacy_mode,
    retention=retention,
    trace_mode=trace_mode,
    audit_color=audit_color,
    parent_dna=parent_dna,
    confirm=confirm,
    seal=seal
)
```

def record_to_json(record: DynamicDNARecord) -> str:

```python
return json.dumps(asdict(record), ensure_ascii=False, indent=2)
```


---


### 3.4.7 Verification Algorithm

Generating DNA is only half of the mechanism. A verifier must be able to parse and validate the record.

Algorithm 3: VerifyDynamicDNA

def verify_dynamic_dna(

```python
artifact: str,
record: DynamicDNARecord,
claimed_uid: str,
claimed_gpg_prefix: str,
```

) -> tuple[float, list[str]]:

```python
"""
Verify that a Dynamic DNA record is consistent with the artifact and claimed identity.
Returns a score and evidence log.
"""
evidence: list[str] = []
# 1. Prefix and UID check
if not record.dna.startswith("#龍芯⚡️"):
    return 0.0, ["DNA prefix mismatch"]
if record.uid != claimed_uid:
    return 0.0, ["UID mismatch"]
evidence.append("DNA prefix and UID verified")
# 2. GPG prefix check
if record.gpg_prefix != claimed_gpg_prefix[:8].upper():
    return 0.0, ["GPG prefix mismatch"]
if record.gpg_prefix not in record.dna:
    return 0.0, ["GPG prefix missing from DNA string"]
evidence.append("GPG prefix verified")
# 3. Artifact hash check
# ... (22 行代码省略) ...
evidence.append("Digit root, wuxing, and audit route verified")
# 6. Privacy consistency check
if record.privacy_mode == "sealed" and record.retention != "hash_only":
    return 0.0, ["Sealed content must use hash_only retention"]
if record.privacy_mode == "burn" and record.retention == "full":
    return 0.0, ["Burn content must not use full retention"]
if record.trace_mode == "no_external" and record.retention == "full":
    evidence.append("Warning: no_external content should avoid full retention in external contexts")
evidence.append("Privacy and retention consistency checked")
return 1.0, evidence
```


---


### 3.4.8 Append-Only Ledger Integration

Dynamic DNA becomes stronger when written into an append-only ledger.

Ledger Entry Format

{

"event": "DYNAMIC_DNA_GENERATED",

"dna": "#龍芯⚡️2026-05-04-午时-金-BEHAVIORAL-VERIFY-A2D0092C-7FA3C91B",

"parent_dna": "#龍芯⚡️2026-05-04-BEHAVIORAL-CRYPTOGRAPHY-THREAT-MODEL-v1.0",

"artifact_hash": "sha256:7fa3c91b84d5...",

"module": "BEHAVIORAL-VERIFY",

"action": "CREATE_SECTION",

"ts": "2026-05-04T12:30:00+08:00",

"operator": "UID9622",

"audit_color": "🟢",

"previous_log_hash": "sha256:...",

"current_log_hash": "sha256:..."

}

Hash-Chain Update

def hash_ledger_entry(entry: dict, previous_hash: str) -> str:

```python
canonical = json.dumps(
    {**entry, "previous_log_hash": previous_hash},
    ensure_ascii=False,
    sort_keys=True
)
return "sha256:" + hashlib.sha256(canonical.encode("utf-8")).hexdigest()
```

This allows later verification:

ledger_verification:

- check_entry_exists
- check_previous_hash_matches
- recompute_current_hash
- confirm_parent_child_link
- confirm_timestamp_order


---


### 3.4.9 Privacy Modes in DNA Generation

The DNA Engine must not leak private content.

Normal Mode

Used for public or internal non-sensitive material.

allow_summary: true

dna_includes: ["date", "module", "action", "hash8"]

Burn Mode

Used for temporary sensitive material.

burn_mode:

dna_includes: ["date", "module", "action", "hash8"]

Sealed Mode

Used for secrets, keys, private tokens, confidential materials, or suspected classified content.

sealed_mode:

dna_includes: ["date", "sealed", "hash8"]

Critical rule:

Dynamic DNA must never become a reason to expose the content it is supposed to protect.


---


### 3.4.10 Dynamic DNA and the Seven-Factor Framework

Dynamic DNA directly supports multiple verification factors.

Factor Supported By Dynamic DNA

F1 Identity DNA UID, GPG prefix, seal, confirm

F2 Temporal Anchor ISO time, date, shichen, digit root

F3 Rule Trace module, action, parent DNA, ledger entry

F4 Persona Route can include persona route DNA in parent chain

F5 Protected Lexicon DNA can bind protected lexicon version

F6 Style Vector can reference baseline corpus hash

F7 Mistake Ledger can reference mistake ledger snapshot hash

Dynamic DNA is therefore not a replacement for all seven factors. It is the root record that helps connect them.

Academic phrasing:

The Dynamic DNA Engine acts as a provenance coordination layer rather than a complete authentication system by itself.

UID9622 说法：

DNA 是门牌号，不是整栋楼；但没门牌，后面七层证据就不好找。


---


### 3.4.11 Security Analysis

Property 1: Artifact Binding

If the artifact changes, its SHA-256 digest changes. Therefore, the DNA record no longer verifies.

artifact ≠ artifact' => hash(artifact) ≠ hash(artifact')

Within standard cryptographic assumptions, collision probability is negligible.

Property 2: Identity Binding

The DNA string includes the UID and GPG prefix. The canonical record includes the full GPG fingerprint.

This does not prove signature validity by itself. It provides a structured identity claim that must be checked against a signature or trusted public record.

Property 3: Temporal Consistency

The DNA record includes ISO time, date, shichen, and digit root. A forged record must keep these fields mutually consistent.

This does not prevent a local attacker from creating a false timestamp unless the ledger is externally anchored. It does, however, increase inconsistency detection when combined with append-only logs.

Property 4: Lineage Continuity

Parent DNA links create a chain:

DNA_0 -> DNA_1 -> DNA_2 -> ... -> DNA_n

If an attacker removes or changes an intermediate record, the chain becomes inconsistent unless they can rewrite all subsequent anchored entries.

Property 5: Privacy Preservation

Only hashes and metadata need to be stored for sensitive content. The engine supports sealed and burn modes to avoid storing raw private text.


---


### 3.4.12 Limitations

The Dynamic DNA Engine has explicit limitations.

limitations:

- DNA strings alone do not replace digital signatures.
- Local timestamps are not trusted unless anchored.
- GPG prefix alone is not full GPG verification.
- Cultural markers are not cryptographic primitives.
- Hashes prove content integrity, not legal ownership.
- If raw artifacts are unavailable, only hash consistency can be checked.
- If private keys are compromised, identity claims must be revoked and rotated.


---


### 3.4.13 Implementation Note: Minimal Local Deployment

A minimal local deployment requires only:

minimal_deployment:

```python
- dynamic_dna_engine.py
- audit_log.jsonl
- dna_registry.json
```

```python
- gpg_signature.asc
- public_checkpoint.txt
- protected_lexicon.json
- persona_registry.json
```

Recommended local folder:

behavioral_crypto/

dynamic_dna_engine.py

dna_registry.json

audit_log.jsonl

protected_lexicon.json

persona_registry.json

tests/

```python
test_dynamic_dna.py
test_dna_verification.py
```


---


### 3.4.14 Transition to Section 3.5

The Dynamic DNA Engine provides the root provenance identifier. The next section introduces how such identifiers are embedded into a complete behavioral evidence chain through rule traces, persona routes, protected lexicons, and mistake ledgers.
