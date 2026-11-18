<!--
DNA: #龍芯⚡️2026-11-18-BEHAVIORAL-CRYPTOGRAPHY-FULL-PAPER-v1.0
GPG: A2D0092CEE2E5BA87035600924C3704A8CC26D5F
CONFIRM: #CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z
SEAL: #ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL
License: CC BY-NC-SA 4.0 + Longhun DNA Inheritance Clause
Part of: Behavioral Cryptography Full Paper v1.0 (see README.md)
-->

# Appendix B: Proof Bundle Schema


附录 B：证据包标准结构

## B.1 Purpose

The Proof Bundle is a portable evidence package for Behavioral Cryptography. It allows a creator to export, review, redact, verify, and submit provenance evidence without requiring full exposure of private drafts or sealed records.

**中文注：**

Proof Bundle 是“证据包”，不是“聊天记录全公开”。它的核心是：能证明血统，但不强迫泄露隐私。


---


## B.2 Proof Bundle JSON Schema v1.0

{

"schema": "LONGHUN_BEHAVIORAL_CRYPTOGRAPHY_PROOF_BUNDLE",

"version": "v1.0",

"bundle_id": "BC-PROOF-UID9622-YYYYMMDD-HASH8",

"created_at": "2026-05-04T00:00:00+08:00",

"originator": {

```python
"uid": "UID9622",
"display_name": "Zhuge Xin / 諸葛鑫 / 龍芯北辰",
"gpg_fingerprint": "A2D0092CEE2E5BA87035600924C3704A8CC26D5F",
"public_claim": "Human originator and system architect"
```

},

"artifact": {

```python
"title": "Behavioral Cryptography",
"artifact_type": "paper",
"content_hash": "sha256:PLACEHOLDER",
"metadata_hash": "sha256:PLACEHOLDER",
"language": ["en", "zh"],
"license": "CC BY-NC-SA 4.0 + Longhun DNA Inheritance Clause"
```

},

"behavioral_signature": {

```python
"F1_identity_dna": {
  "dna": "#龍芯⚡️2026-05-02-BEHAVIORAL-CRYPTOGRAPHY-PAPER-v1.0",
  "uid": "UID9622",
  "gpg_fingerprint": "A2D0092CEE2E5BA87035600924C3704A8CC26D5F"
},
"F2_temporal_anchor": {
  "iso_time": "2026-05-02T00:00:00+08:00",
  "shichen": "PLACEHOLDER",
  "digit_root": "PLACEHOLDER",
  "timezone": "Asia/Shanghai"
},
"F3_rule_trace": [
  {
    "rule_id": "UID9622-UNIVERSAL-CNSH-ROOT-AUDIT",
    "rule_dna": "#龍芯⚡️2026-05-04-UNIVERSAL-CNSH-ROOT-AUDIT-v1.2",
    "timestamp": "2026-05-04T00:00:00+08:00",
    "action": "applied"
  }
# ... (28 行代码省略) ...
  "note": "Full vector may be sealed or restricted."
},
"F7_mistake_ledger": [
  {
    "mistake_id": "ML-PLACEHOLDER-001",
    "category": "AI_FORMAT_DRIFT",
    "correction": "Enforced one-pass output format",
    "timestamp": "2026-05-04T00:00:00+08:00"
  }
]
```

},

"ai_collaboration": {

```python
"ai_systems": [
  {
    "name": "Claude",
    "role": "formalization and polishing",
    "root_author": false
  },
  {
    "name": "ChatGPT",
    "role": "structuring and verification assistance",
    "root_author": false
  }
],
"human_originator": "UID9622",
"human_oversight": true
```

},

"disclosure_policy": {

```python
"public_fields": [
  "originator",
  "artifact",
  "F1_identity_dna",
  "F5_protected_lexicon",
  "ai_collaboration"
],
"restricted_fields": [
  "F3_rule_trace",
  "F4_persona_route",
  "F7_mistake_ledger"
],
"sealed_fields": [
  "private drafts",
  "sensitive conversations",
  "local-only logs",
  "raw style vectors"
]
```

},

"root_card": {

```python
"Root": "dr=5",
"Wuxing": "土",
"TriColor": "🟢",
"PrivacyMode": "normal",
"Retention": "summary_only",
"TraceMode": "chain"
```

},

"confirm": "#CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z",

"seal": "#ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL"

}


---


## B.3 Required vs Optional Fields

Field Required Reason

schema Yes identifies standard

version Yes supports future evolution

originator.uid Yes binds human originator

originator.gpg_fingerprint Yes cryptographic anchor

artifact.content_hash Yes content integrity

F1_identity_dna Yes root identity factor

F2_temporal_anchor Recommended time lineage

F3_rule_trace Recommended process lineage

F4_persona_route Optional multi-agent route

F5_protected_lexicon Yes anti-laundering terms

F6_style_vector Optional / restricted stylistic continuity

F7_mistake_ledger Recommended / restricted honesty signal

ai_collaboration Yes if AI used co-authorship transparency

disclosure_policy Yes privacy boundary

confirm / seal Yes for Longhun bundle ownership continuity


---
