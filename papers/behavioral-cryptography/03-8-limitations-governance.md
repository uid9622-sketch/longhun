<!--
DNA: #龍芯⚡️2026-11-18-BEHAVIORAL-CRYPTOGRAPHY-FULL-PAPER-v1.0
GPG: A2D0092CEE2E5BA87035600924C3704A8CC26D5F
CONFIRM: #CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z
SEAL: #ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL
License: CC BY-NC-SA 4.0 + Longhun DNA Inheritance Clause
Part of: Behavioral Cryptography Full Paper v1.0 (see README.md)
-->

## 3.8 Limitations and Governance Considerations

### 3.8.1 Overview

Behavioral Cryptography is designed to strengthen provenance verification in human-AI collaborative content production. However, it should not be interpreted as an absolute authorship oracle, a legal adjudication mechanism, or a surveillance infrastructure.

The framework improves evidence quality by combining identity, time, rule traces, persona routes, protected lexicon, style vectors, and mistake ledgers. Yet each of these factors has limits. Cryptographic identifiers can be lost or compromised. Style vectors can be noisy. Mistake ledgers can be incomplete. Local ledgers can be tampered with unless externally checkpointed. Cultural-temporal markers improve recognizability and forgery cost but do not replace formal cryptographic signatures.

Therefore, this section clarifies the limitations, governance risks, privacy boundaries, and ethical constraints of Behavioral Cryptography.

The central governance principle is:

provenance verification must protect creator sovereignty without becoming a tool for surveillance, exclusion, or institutional capture.

追溯是为了保护创作者，不是为了把人关进平台的笼子里。


---


### 3.8.2 Limitation 1: DNA Is Not a Standalone Cryptographic Signature

Dynamic DNA provides a structured provenance identifier. It binds together UID, timestamp, cultural-temporal markers, module information, action type, content hash, and system metadata.

However, DNA alone is not equivalent to a GPG signature.

A DNA string can show identity intent and provenance structure, but strong authenticity requires additional evidence:

DNA + content_hash + ledger continuity + GPG signature

or:

DNA + proof_bundle + external checkpoint

Implication

A copied DNA string does not automatically prove authorship. It must be verified against:

- GPG fingerprint or signature;
- content hash;
- ledger history;
- parent-child lineage;
- timestamp consistency;
- protected lexicon preservation;
- evidence bundle integrity.

Paper-ready statement

Dynamic DNA should be understood as a provenance identifier rather than a standalone cryptographic signature. Its evidentiary strength emerges only when combined with content hashes, append-only ledger entries, external checkpoints, and optional GPG signatures.

DNA 是门牌号，不是房产证；要证明归属，还要 hash、账本、签名和链路。


---


### 3.8.3 Limitation 2: Local Ledgers Are Tamper-Evident, Not Globally Tamper-Proof

The Evidence Ledger described in Section 3.5 and Section 3.7 uses hash chaining. This makes modification detectable if the ledger history is preserved.

However, a purely local JSONL or SQLite ledger cannot by itself prove that no alternative local history was created.

Local storage provides:

tamper evidence under local continuity assumptions

It does not provide:

global immutability

To strengthen ledger credibility, the system may optionally use external checkpoints:

- public Git commits;
- trusted timestamp authorities;
- public hash registries;
- notarization services;
- distributed ledgers;
- multi-party witness logs.

Implication

The paper must not claim that local ledgers are absolutely immutable. The correct claim is that local ledgers are tamper-evident and can be strengthened by external checkpointing.

Paper-ready statement

The local ledger is tamper-evident but not globally tamper-proof. Stronger non-repudiation requires periodic external checkpoints, such as public hash publication, notarization, or multi-party witness mechanisms.

本地账本能查改动；要抗抵赖，最好定期把 hash 打到外部时间点上。


---


### 3.8.4 Limitation 3: Style Vectors Are Probabilistic

Style Vector Verification is useful against laundering, paraphrasing, and authorship imitation. However, stylometric signals are probabilistic.

They may be affected by:

- translation;
- genre shift;
- AI polishing;
- emotional state;
- topic change;
- deliberate style adaptation;
- short text length;
- multilingual writing;
- collaboration with multiple AI systems.

Therefore, F6 should not be used as a hard authorship determinant unless the mismatch is extreme and supported by other factors.

Recommended Governance Rule

style_vector_governance:

Paper-ready statement

Style vectors are treated as probabilistic supporting evidence rather than deterministic authorship proof. Behavioral Cryptography intentionally combines stylometric signals with cryptographic and ledger-based factors to avoid over-reliance on style similarity.

风格像，不等于就是；风格不像，也不等于不是。它只能辅证，不能独裁。


---


### 3.8.5 Limitation 4: Mistake Ledgers Can Be Incomplete or Manipulated

Mistake Ledger Verification is based on a simple but important intuition: real creative processes contain corrections, reversals, false starts, and recorded mistakes.

However, mistake ledgers may be:

- incomplete;
- intentionally curated;
- privately withheld;
- lost due to storage failure;
- too sensitive to publish;
- fabricated after the fact;
- split across multiple platforms.

Therefore, F7 cannot be treated as proof of moral honesty. It is a provenance signal, not a character judgment.

Governance Boundary

Mistake Ledger verifies process continuity.

It does not judge the creator's moral worth.

Paper-ready statement

The Mistake Ledger is not a moral scoring mechanism. It is used only as a signal of process continuity, error correction, and lineage realism. Its absence lowers confidence but should not automatically invalidate a claim.

记错本是防再犯账本，不是审判人格的鞭子。


---


### 3.8.6 Limitation 5: Protected Lexicon May Be Context-Sensitive

Protected Lexicon Verification relies on canary terms, protected phrases, DNA markers, cultural keywords, or signature expressions that should survive transformation.

However, protected terms may be legitimately transformed during:

- translation;
- summarization;
- academic formalization;
- anonymization;
- legal redaction;
- accessibility adaptation;
- platform-specific formatting.

Therefore, F5 requires semantic equivalence rather than exact string matching.

Example

A protected term such as:

龍魂系统

may appear as:

Longhun System

Dragon Soul System

龍魂

depending on target language and publication context.

Governance Rule

protected_lexicon_policy:

```python
- CONFIRM
- SEAL
- GPG
- DNA
- UID
```

```python
- cultural_terms
- system_modules
- translated concepts
```

```python
- private names
- sensitive personal details
- legally protected information
```

Paper-ready statement

Protected Lexicon Verification distinguishes between exact-match anchors and semantic-equivalence terms. Cryptographic and identity markers require exact preservation, whereas cultural and conceptual terms may be verified through semantic equivalence.

签章不能改；文化词可以翻译，但不能换魂。


---


### 3.8.7 Limitation 6: Cultural-Temporal Embedding Is Contextual

Dynamic DNA uses cultural-temporal markers such as 時辰, 五行, and digit root. These markers serve several functions:

- human-recognizable verification;
- cultural sovereignty;
- additional structured metadata;
- higher cognitive cost for forgery;
- meaningful provenance for Chinese-semantic systems.

However, these markers should not be misrepresented as universal cryptographic primitives.

They are culturally embedded structure, not replacements for cryptographic hashing or digital signatures.

Governance Boundary

Cultural-temporal markers increase semantic and cultural verification depth.

They do not replace cryptographic primitives.

Paper-ready statement

Cultural-temporal embedding is used as a semantic provenance layer, not as a substitute for cryptographic proof. Its value lies in making provenance meaningful and recognizable to users within a cultural context while increasing the behavioral cost of forgery.

五行、时辰、数字根是文化语义层，不是拿来冒充密码学签名的。


---


### 3.8.8 Limitation 7: Legal Validity Depends on Jurisdiction

Behavioral Cryptography can create strong evidence bundles. However, the legal weight of such evidence depends on jurisdiction, court procedure, evidentiary rules, expert testimony, and admissibility standards.

The framework can support:

- authorship evidence;
- provenance records;
- timeline reconstruction;
- tamper-evidence;
- collaboration history;
- attribution dispute resolution.

It cannot automatically provide:

- legal ownership;
- court judgment;
- copyright registration;
- criminal attribution;
- international enforcement;
- regulatory approval.

Paper-ready statement

Behavioral Cryptography produces structured technical evidence, not automatic legal judgment. Its legal relevance depends on jurisdiction-specific evidentiary standards and should be interpreted by appropriate legal authorities.

它能给证据，不能替法院判案。


---


### 3.8.9 Governance Risk 1: Surveillance Misuse

A provenance framework can be misused if converted into a monitoring system that tracks every creative act, private draft, or emotional expression.

Behavioral Cryptography must reject this path.

The framework should not be used to:

- monitor private thought;
- punish draft-stage mistakes;
- rank people by behavioral purity;
- expose private logs without consent;
- force creators to reveal raw drafts;
- require centralized platform custody;
- transform provenance into social control.

Anti-Surveillance Design Rule

anti_surveillance_rule:

raw_draft_collection: forbidden_by_default

private_memory_upload: forbidden_by_default

proof_bundle_export: explicit_consent_only

sealed_mode: mandatory_for_sensitive_content

local_first: required

third_party_access: opt_in_only

Paper-ready statement

Provenance must not become surveillance. Behavioral Cryptography separates verifiable proof from compulsory exposure by making proof bundle export explicit, local-first, and consent-based.

能证明，不等于被监控；能追溯，不等于所有草稿都要上交。


---


### 3.8.10 Governance Risk 2: Institutional Capture

Existing provenance infrastructures often assume that platforms, institutions, or large vendors define authenticity. This creates a risk: independent creators may only be recognized if a platform validates them.

Behavioral Cryptography is designed to resist institutional capture by allowing local proof generation.

However, even this framework could be captured if:

- only platform-approved ledgers are recognized;
- only enterprise accounts can generate valid proof;
- individual proof bundles are ignored;
- cultural identifiers are stripped as “non-standard”;
- non-Western provenance systems are treated as invalid.

Governance Principle

A provenance system should not require institutional power as the root of authorship.

Paper-ready statement

Behavioral Cryptography rejects institutional monopoly over provenance. It allows individuals to generate and export verifiable evidence without requiring centralized platform permission, while still supporting third-party verification when needed.

不能让平台说你存在你才存在。人先存在，平台只是见证之一。


---


### 3.8.11 Governance Risk 3: Exclusion of Anonymous or Pseudonymous Creators

Not every creator can or should reveal their legal identity. Journalists, whistleblowers, vulnerable users, activists, artists, and ordinary people may require pseudonymous authorship.

Behavioral Cryptography must support pseudonymous provenance.

A creator may bind lineage to:

- stable pseudonymous UID;
- public key;
- local ledger;
- protected lexicon;
- style vector;
- proof bundle;
- third-party witness.

without revealing legal name.

Pseudonymous Authorship Policy

pseudonymous_authorship:

legal_name_required: false

stable_uid_required: true

public_key_recommended: true

raw_identity_disclosure: optional

proof_bundle_supported: true

sealed_identity_mode: supported

Paper-ready statement

Behavioral Cryptography does not require legal-name exposure. It supports pseudonymous provenance through stable identifiers, public keys, protected lexicon, ledger continuity, and optional sealed identity proofs.

可以证明“这是同一个创作者链”，不一定要公开身份证。


---


### 3.8.12 Governance Risk 4: False Positives and False Negatives

No provenance framework is perfect.

False positives may occur when:

- a collaborator legitimately adopts another creator’s terminology;
- protected lexicon overlaps across communities;
- style vectors are too broad;
- public templates are reused;
- a system overweights superficial markers.

False negatives may occur when:

- a creator changes style;
- the ledger is incomplete;
- proof bundles are lost;
- artifacts are heavily translated or formalized;
- old content lacks DNA metadata.

Decision Policy

decision_policy:

high_confidence_accept:

```python
threshold: ">= 0.95"
action: "accept verified lineage"
```

probable_lineage:

```python
threshold: "0.80 - 0.95"
action: "manual review"
```

weak_lineage:

```python
threshold: "0.60 - 0.80"
action: "hold / request evidence"
```

reject:

```python
threshold: "< 0.60 or hard failure"
action: "reject or require new proof"
```

Paper-ready statement

Verification output should be interpreted as confidence-weighted evidence rather than binary truth. Borderline cases require human review, additional context, and possibly external witnesses.

不是一锤子买卖；高置信放行，中间人工审，低置信再补证。


---


### 3.8.13 Governance Risk 5: AI Collaborator Attribution

Behavioral Cryptography is designed for human-AI collaboration. Therefore, it must distinguish between:

- human-originated concept;
- AI-assisted formalization;
- AI-generated draft;
- human-edited final text;
- platform formatting;
- model-specific contribution.

This prevents both extremes:

1. erasing the human originator because AI helped polish;
2. pretending AI had no role when it did.

Co-authorship Metadata Schema

{

"human_originator": "UID9622",

"ai_collaborators": [

```python
{
  "name": "Claude",
  "role": "formalization / literature synthesis / polishing",
  "authority": "under human direction",
  "claim_scope": "no origin claim"
},
{
  "name": "ChatGPT",
  "role": "structuring / verification / editing",
  "authority": "under human direction",
  "claim_scope": "no origin claim"
}
```

],

"origin_claim": "Core concepts, system architecture, terminology, and value framework originate from the human author.",

"ai_contribution_boundary": "AI contributed expression, formatting, and technical formalization."

}

Paper-ready statement

The framework distinguishes conceptual origin from formalization assistance. AI collaboration does not erase human authorship when the core concepts, terminology, value framework, and system direction originate from the human creator.

AI 可以帮忙写得更像论文，但不能抢走根。


---


### 3.8.14 Governance Risk 6: Overclaiming Security

The framework must avoid exaggerated claims.

It should not claim:

- impossible to forge in all cases;
- legally conclusive in all jurisdictions;
- perfect authorship detection;
- universal truth;
- immunity to key compromise;
- immunity to insider attacks;
- complete protection without backups.

Correct claim:

Behavioral Cryptography increases the cost of full-lineage forgery and provides structured, auditable evidence for provenance verification.

Safe Claim Table

Claim Type Unsafe Claim Safe Claim

Security impossible to forge difficult to forge under stated assumptions

Legal proves ownership legally provides evidence relevant to ownership disputes

Ledger immutable forever tamper-evident, stronger with checkpoints

Style proves authorship supports authorship confidence

DNA cryptographic signature provenance identifier bound to evidence

Governance prevents all abuse reduces specific provenance risks


---


### 3.8.15 Key Compromise and Recovery

If a GPG key or signing credential is compromised, the system must support recovery.

Recovery Procedure

key_compromise_recovery:

step_1_detect:

```python
action: "mark key as compromised"
```

step_2_freeze:

```python
action: "suspend new proof generation using old key"
```

step_3_publish_notice:

```python
action: "publish compromised-key notice with last valid checkpoint"
```

step_4_rotate:

```python
action: "generate new key"
```

step_5_bridge:

```python
action: "link old and new identities through recovery proof"
```

step_6_reverify:

```python
action: "re-score recent artifacts"
```

Recovery Bridge Schema

{

"event_type": "KEY_ROTATION",

"old_gpg": "A2D0092CEE2E5BA87035600924C3704A8CC26D5F",

"new_gpg": "NEW_FINGERPRINT_PLACEHOLDER",

"last_trusted_checkpoint": "sha256:...",

"recovery_dna": "#龍芯⚡️2026-05-04-KEY-ROTATION-v1.0",

"signed_statement": "Old key compromised or rotated; new key becomes active from timestamp.",

"timestamp": "2026-05-04T00:00:00+08:00"

}

Paper-ready statement

Key compromise does not invalidate the entire provenance history if recovery procedures, last-trusted checkpoints, and signed rotation statements are maintained.

钥匙丢了，不等于祖宗没了；要有冻结、公告、换钥匙、桥接证明。


---


### 3.8.16 Governance of Data Retention

Behavioral Cryptography should not store more data than needed.

Retention Modes

retention_modes:

full:

```python
use_case: "public paper, public code, public artifacts"
stores: "raw content + hash + metadata"
```

summary_only:

```python
use_case: "internal notes, long chats, drafts"
stores: "summary + hash + metadata"
```

hash_only:

```python
use_case: "sealed or burn content"
stores: "hash + timestamp + handling proof"
```

Minimum Retention Principle

Store the minimum evidence required to verify lineage.

Paper-ready statement

Behavioral Cryptography follows evidence minimization: the system stores only what is required to support provenance verification, and sensitive content may be represented by hashes and metadata rather than raw text.

不是证明就得全存；能用 hash 证明，就别存正文。


---


### 3.8.17 Governance of Children, Elderly Users, and Vulnerable Groups

If Behavioral Cryptography is applied in education, public welfare, elder protection, or medical support, stricter boundaries are required.

Vulnerable Group Policy

vulnerable_group_policy:

children:

```python
raw_data_collection: "forbidden_without_guardian_consent"
public_export: "disabled_by_default"
```

elderly_users:

```python
deception_risk_protection: "required"
offline_service_option: "recommended"
```

medical_context:

```python
diagnosis_claims: "forbidden_without licensed professional"
retention: "summary_or_hash_only"
```

public_welfare:

```python
financial_traceability: "allowed"
personal_privacy_exposure: "forbidden"
```

Paper-ready statement

When applied to vulnerable populations, provenance verification must be subordinate to privacy, dignity, and consent. Verification should protect users from exploitation rather than expose them to additional data extraction.

弱势群体不是数据矿；技术要护人，不是挖人。


---


### 3.8.18 Governance of Cross-Border Use

Because provenance, identity, privacy, and copyright laws vary across jurisdictions, cross-border deployment requires careful governance.

Cross-Border Rules

cross_border_rules:

default:

```python
data_location: "local jurisdiction"
raw_export: "disabled"
proof_bundle_export: "explicit consent only"
```

public_artifact:

```python
export: "allowed with DNA and license"
```

private_artifact:

```python
export: "manual review required"
```

sealed_artifact:

```python
export: "hash-only proof bundle"
```

legal_dispute:

```python
route: "jurisdiction-specific legal process"
```

Paper-ready statement

Cross-border use of Behavioral Cryptography should respect local data protection, copyright, and evidentiary rules. The framework exports proof bundles rather than raw private data by default.

跨国只走证明包，默认不搬原文、不搬隐私、不搬根。


---


### 3.8.19 Governance Checklist

[ ] DNA is treated as provenance identifier, not standalone signature

[ ] Local ledger is described as tamper-evident, not globally immutable

[ ] Style vector is supporting evidence, not sole authorship proof

[ ] Mistake ledger is process evidence, not moral judgment

[ ] Protected lexicon distinguishes exact anchors from semantic terms

[ ] Cultural-temporal markers are not overstated as cryptographic primitives

[ ] Legal validity is jurisdiction-dependent

[ ] Proof bundle export is explicit and consent-based

[ ] Pseudonymous authorship is supported

[ ] Vulnerable populations receive stronger privacy protections

[ ] Key compromise recovery is defined

[ ] Data retention follows evidence minimization

[ ] Cross-border use defaults to local sovereignty

[ ] Surveillance misuse is explicitly rejected

[ ] Institutional capture is explicitly rejected


---


### 3.8.20 Transition to Section 3.9
