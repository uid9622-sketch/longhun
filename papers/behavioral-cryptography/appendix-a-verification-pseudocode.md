<!--
DNA: #龍芯⚡️2026-11-18-BEHAVIORAL-CRYPTOGRAPHY-FULL-PAPER-v1.0
GPG: A2D0092CEE2E5BA87035600924C3704A8CC26D5F
CONFIRM: #CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z
SEAL: #ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL
License: CC BY-NC-SA 4.0 + Longhun DNA Inheritance Clause
Part of: Behavioral Cryptography Full Paper v1.0 (see README.md)
-->

# Appendix A: Behavioral Signature Verification Pseudocode


附录 A：行为签名验证伪代码

## A.1 Purpose

This appendix provides reference pseudocode for verifying a Behavioral Cryptography signature. The goal is not to define a production-ready security library, but to provide a reproducible structure for testing the seven-factor verification framework described in Section 3.

**中文注：**

本附录不是最终生产级密码库，而是给审稿人、开发者、Cursor、本地 Python 模块一个能照着实现的骨架。


---


## A.2 Core Data Structures

from dataclasses import dataclass, field

from typing import Any, Dict, List, Tuple, Optional

from datetime import datetime

import hashlib

import math

@dataclass

class EvidenceItem:

```python
factor: str
score: float
status: str
message: str
metadata: Dict[str, Any] = field(default_factory=dict)
```

@dataclass

class EvidenceLog:

```python
items: List[EvidenceItem] = field(default_factory=list)
def add(self, factor: str, score: float, status: str, message: str, **metadata):
    self.items.append(
        EvidenceItem(
            factor=factor,
            score=score,
            status=status,
            message=message,
            metadata=metadata
        )
    )
def hard_failures(self) -> List[EvidenceItem]:
    return [x for x in self.items if x.score == 0.0]
def to_dict(self) -> Dict[str, Any]:
    return {
        "items": [x.__dict__ for x in self.items],
        "hard_failures": [x.__dict__ for x in self.hard_failures()]
    }
```

@dataclass

class BehavioralSignature:

```python
F1_identity_dna: Dict[str, Any]
F2_temporal_anchor: Dict[str, Any]
F3_rule_trace: List[Dict[str, Any]]
F4_persona_route: List[Dict[str, Any]]
F5_protected_lexicon: List[str]
F6_style_vector: Dict[str, Any]
F7_mistake_ledger: List[Dict[str, Any]]
```

@dataclass

class OriginatorRecord:

```python
uid: str
display_name: str
gpg_fingerprint: str
known_dna_prefixes: List[str]
protected_lexicon: List[str]
baseline_style_vector: Optional[List[float]] = None
```


---


## A.3 Utility Functions

def sha256_text(text: str) -> str:

```python
return hashlib.sha256(text.encode("utf-8", errors="ignore")).hexdigest()
```

def weighted_geometric_mean(scores: List[float], weights: List[float]) -> float:

```python
if len(scores) != len(weights):
    raise ValueError("scores and weights must have equal length")
if any(s == 0.0 for s in scores):
    return 0.0
total_weight = sum(weights)
product = 1.0
for s, w in zip(scores, weights):
    product *= s ** w
return product ** (1.0 / total_weight)
```

def cosine_similarity(a: List[float], b: List[float]) -> float:

```python
if len(a) != len(b) or len(a) == 0:
    return 0.0
dot = sum(x * y for x, y in zip(a, b))
norm_a = math.sqrt(sum(x * x for x in a))
norm_b = math.sqrt(sum(y * y for y in b))
if norm_a == 0.0 or norm_b == 0.0:
    return 0.0
return dot / (norm_a * norm_b)
```

def is_monotonic_timestamps(items: List[Dict[str, Any]]) -> bool:

```python
times = []
for item in items:
    ts = item.get("timestamp")
    if not ts:
        return False
    try:
        times.append(datetime.fromisoformat(ts))
    except Exception:
        return False
return all(times[i] <= times[i + 1] for i in range(len(times) - 1))
```


---


## A.4 Seven-Factor Verification Functions

A.4.1 F1 Identity DNA Verification

def verify_F1_identity_dna(

```python
signature: BehavioralSignature,
originator: OriginatorRecord,
evidence: EvidenceLog
```

) -> float:

```python
f1 = signature.F1_identity_dna
dna = f1.get("dna", "")
claimed_uid = f1.get("uid", "")
claimed_gpg = f1.get("gpg_fingerprint", "")
if not dna.startswith("#龍芯⚡️"):
    evidence.add("F1", 0.0, "FAIL", "DNA prefix mismatch", dna=dna)
    return 0.0
if claimed_uid != originator.uid:
    evidence.add("F1", 0.0, "FAIL", "UID mismatch", claimed_uid=claimed_uid)
    return 0.0
if claimed_gpg.upper() != originator.gpg_fingerprint.upper():
    evidence.add("F1", 0.0, "FAIL", "GPG fingerprint mismatch")
    return 0.0
if originator.uid not in dna and "UID9622" not in dna:
    evidence.add("F1", 0.0, "FAIL", "Originator UID not embedded in DNA")
    return 0.0
evidence.add("F1", 1.0, "PASS", "Identity DNA verified", dna=dna)
return 1.0
```


---


A.4.2 F2 Temporal Anchor Verification

def verify_F2_temporal_anchor(

```python
signature: BehavioralSignature,
originator: OriginatorRecord,
evidence: EvidenceLog,
max_drift_seconds: int = 60
```

) -> float:

```python
f2 = signature.F2_temporal_anchor
iso_time = f2.get("iso_time")
shichen = f2.get("shichen")
digit_root = f2.get("digit_root")
if not iso_time:
    evidence.add("F2", 0.0, "FAIL", "Missing ISO timestamp")
    return 0.0
try:
    dt = datetime.fromisoformat(iso_time)
except Exception:
    evidence.add("F2", 0.0, "FAIL", "Invalid ISO timestamp", iso_time=iso_time)
    return 0.0
if shichen is None:
    evidence.add("F2", 0.0, "FAIL", "Missing shichen anchor")
    return 0.0
if digit_root is None:
    evidence.add("F2", 0.0, "FAIL", "Missing digit root")
    return 0.0
evidence.add(
    "F2",
    1.0,
    "PASS",
    "Temporal anchor verified",
    iso_time=iso_time,
    shichen=shichen,
    digit_root=digit_root
)
return 1.0
```


---


A.4.3 F3 Rule Trace Verification

def verify_F3_rule_trace(

```python
signature: BehavioralSignature,
originator: OriginatorRecord,
evidence: EvidenceLog
```

) -> float:

```python
trace = signature.F3_rule_trace
if not trace:
    evidence.add("F3", 0.4, "WEAK", "No rule trace provided")
    return 0.4
if not is_monotonic_timestamps(trace):
    evidence.add("F3", 0.0, "FAIL", "Rule trace timestamps are not monotonic")
    return 0.0
missing_dna = [
    r for r in trace
    if not r.get("rule_dna") or not str(r.get("rule_dna")).startswith("#龍芯⚡️")
]
if missing_dna:
    evidence.add("F3", 0.0, "FAIL", "Rule trace contains missing or invalid DNA")
    return 0.0
evidence.add(
    "F3",
    1.0,
    "PASS",
    "Rule trace verified",
    count=len(trace)
)
return 1.0
```


---


A.4.4 F4 Persona Route Verification

def verify_F4_persona_route(

```python
signature: BehavioralSignature,
originator: OriginatorRecord,
evidence: EvidenceLog
```

) -> float:

```python
route = signature.F4_persona_route
if not route:
    evidence.add("F4", 0.5, "WEAK", "No persona route provided")
    return 0.5
invalid = [
    p for p in route
    if not p.get("persona_id") or not p.get("role")
]
if invalid:
    evidence.add("F4", 0.0, "FAIL", "Invalid persona route item")
    return 0.0
evidence.add(
    "F4",
    0.95,
    "PASS",
    "Persona route verified",
    route=[p.get("persona_id") for p in route]
)
return 0.95
```


---


A.4.5 F5 Protected Lexicon Verification

def verify_F5_protected_lexicon(

```python
content: str,
signature: BehavioralSignature,
originator: OriginatorRecord,
evidence: EvidenceLog,
critical_threshold: float = 0.30
```

) -> float:

```python
protected_terms = signature.F5_protected_lexicon or originator.protected_lexicon
if not protected_terms:
    evidence.add("F5", 0.6, "WEAK", "No protected lexicon provided")
    return 0.6
missing = []
for term in protected_terms:
    if term not in content:
        missing.append(term)
violation_ratio = len(missing) / max(len(protected_terms), 1)
if violation_ratio > critical_threshold:
    evidence.add(
        "F5",
        0.0,
        "FAIL",
        "Critical protected lexicon violation",
        missing=missing,
        violation_ratio=violation_ratio
    )
    return 0.0
score = 1.0 - 0.8 * violation_ratio
evidence.add(
    "F5",
    score,
    "PASS",
    "Protected lexicon verified",
    missing=missing,
    violation_ratio=violation_ratio
)
return score
```


---


A.4.6 F6 Style Vector Verification

def verify_F6_style_vector(

```python
signature: BehavioralSignature,
originator: OriginatorRecord,
evidence: EvidenceLog,
min_similarity: float = 0.75
```

) -> float:

```python
current_vec = signature.F6_style_vector.get("current_vector")
baseline_vec = originator.baseline_style_vector
if not current_vec or not baseline_vec:
    evidence.add("F6", 0.6, "WEAK", "Missing style vector or baseline")
    return 0.6
sim = cosine_similarity(current_vec, baseline_vec)
if sim < min_similarity:
    evidence.add(
        "F6",
        0.0,
        "FAIL",
        "Style vector mismatch",
        similarity=sim
    )
    return 0.0
evidence.add(
    "F6",
    sim,
    "PASS",
    "Style vector verified",
    similarity=sim
)
return sim
```


---


A.4.7 F7 Mistake Ledger Verification

def verify_F7_mistake_ledger(

```python
signature: BehavioralSignature,
originator: OriginatorRecord,
evidence: EvidenceLog
```

) -> float:

```python
ledger = signature.F7_mistake_ledger
if not ledger:
    evidence.add(
        "F7",
        0.7,
        "WEAK",
        "No mistake ledger; possible clean-room laundering or insufficient history"
    )
    return 0.7
if not is_monotonic_timestamps(ledger):
    evidence.add("F7", 0.0, "FAIL", "Mistake ledger timestamps are inconsistent")
    return 0.0
invalid = [
    x for x in ledger
    if not x.get("mistake_id") or not x.get("correction")
]
if invalid:
    evidence.add("F7", 0.0, "FAIL", "Mistake ledger contains invalid entries")
    return 0.0
evidence.add(
    "F7",
    0.95,
    "PASS",
    "Honest mistake ledger verified",
    count=len(ledger)
)
return 0.95
```


---


## A.5 Composite Verification Algorithm

def behavioral_signature_verify(

```python
content: str,
signature: BehavioralSignature,
originator: OriginatorRecord
```

) -> Tuple[float, EvidenceLog]:

```python
evidence = EvidenceLog()
scores = [
    verify_F1_identity_dna(signature, originator, evidence),
    verify_F2_temporal_anchor(signature, originator, evidence),
    verify_F3_rule_trace(signature, originator, evidence),
    verify_F4_persona_route(signature, originator, evidence),
    verify_F5_protected_lexicon(content, signature, originator, evidence),
    verify_F6_style_vector(signature, originator, evidence),
    verify_F7_mistake_ledger(signature, originator, evidence),
]
if any(s == 0.0 for s in scores):
    evidence.add(
        "COMPOSITE",
        0.0,
        "FAIL",
        "Hard failure detected; composite confidence forced to 0.0",
        scores=scores
    )
    return 0.0, evidence
weights = [0.25, 0.15, 0.15, 0.12, 0.12, 0.11, 0.10]
conf = weighted_geometric_mean(scores, weights)
evidence.add(
    "COMPOSITE",
    conf,
    "PASS",
    "Composite verification complete",
    scores=scores,
    weights=weights
)
return conf, evidence
```


---


## A.6 Minimum Test Cases

def test_hard_failure_for_wrong_gpg():

```python
# Expected: conf == 0.0
pass
```

def test_missing_protected_lexicon():

```python
# Expected: F5 hard failure if violation_ratio > 0.30
pass
```

def test_valid_signature_bundle():

```python
# Expected: conf >= 0.95
pass
```

def test_missing_mistake_ledger_is_weak_not_fail():

```python
# Expected: F7 score == 0.7, not hard failure
pass
```

def test_rule_trace_order_violation():

```python
# Expected: F3 hard failure
pass
```


---
