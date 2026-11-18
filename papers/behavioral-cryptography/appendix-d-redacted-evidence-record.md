<!--
DNA: #龍芯⚡️2026-11-18-BEHAVIORAL-CRYPTOGRAPHY-FULL-PAPER-v1.0
GPG: A2D0092CEE2E5BA87035600924C3704A8CC26D5F
CONFIRM: #CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z
SEAL: #ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL
License: CC BY-NC-SA 4.0 + Longhun DNA Inheritance Clause
Part of: Behavioral Cryptography Full Paper v1.0 (see README.md)
-->

# Appendix D: Sample Redacted Evidence Record


附录 D：脱敏证据样例

## D.1 Purpose

This appendix gives an example of how a creator can submit evidence without exposing private conversations, raw drafts, API keys, local paths, or sealed logs.

**中文注：**

给别人看的不是全部原始记录，而是脱敏后仍可验证的证据样本。


---


## D.2 Redacted Evidence Record Example

{

"record_type": "LONGHUN_REDACTED_EVIDENCE_RECORD",

"version": "v1.0",

"record_id": "RED-EVIDENCE-UID9622-20260504-HASH8",

"originator": {

```python
"uid": "UID9622",
"display_name": "Zhuge Xin / 龍芯北辰",
"gpg_fingerprint": "A2D0092CEE2E5BA87035600924C3704A8CC26D5F"
```

},

"artifact": {

```python
"title": "Behavioral Cryptography",
"section": "3.2 Seven-Factor Verification Mechanism",
"artifact_hash": "sha256:REDACTED_HASH",
"created_range": {
  "start": "2026-05-02T00:00:00+08:00",
  "end": "2026-05-04T00:00:00+08:00"
}
```

},

"evidence_summary": {

```python
"root_concept_origin": "human-originated",
"ai_role": "formalization and polishing",
"protected_terms_preserved": [
  "Behavioral Cryptography",
  "Longhun System",
  "UID9622",
  "Mistake Ledger",
  "Protected Lexicon",
  "Lineage Verification"
],
"rule_trace_available": true,
"persona_route_available": true,
"mistake_ledger_available": true
```

},

"redactions": [

```python
{
  "field": "private_conversation_raw",
  "reason": "private personal context",
  "retention": "hash_only"
},
{
  "field": "local_file_paths",
  "reason": "local device privacy",
  "retention": "summary_only"
},
{
  "field": "sealed_logs",
  "reason": "contains sensitive operational context",
  "retention": "hash_only"
}
```

],

"verification_material": {

```python
"public_dna": "#龍芯⚡️2026-05-02-BEHAVIORAL-CRYPTOGRAPHY-PAPER-v1.0",
"section_dna": "#龍芯⚡️2026-05-04-BEHAVIORAL-CRYPTOGRAPHY-SECTION-3.2-v1.3",
"confirm": "#CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z",
"seal": "#ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL",
"hash_chain_root": "sha256:REDACTED_CHAIN_ROOT"
```

},

"review_mode": {

```python
"public_review": true,
"restricted_review_available": true,
"sealed_review_requires_originator_consent": true
```

}

}


---


## D.3 Redaction Rules

redaction_rules:

never_disclose:

```python
- private keys
- tokens
- passwords
- raw private conversations
- sealed local logs
- unrelated personal data
```

may_disclose_as_hash:

```python
- private drafts
- local audit chain
- sensitive correction logs
- private persona route details
```

may_disclose_as_summary:

```python
- AI collaboration role
- protected lexicon list
- section-level history
- high-level correction history
```

may_disclose_publicly:

```python
- public DNA
- public artifact hash
- authorship declaration
- AI collaboration declaration
- license
```


---
