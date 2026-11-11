# LongHun (龍魂)

**A system may unify its entry points. It must never concentrate power over people's data.**

LongHun is an open, sovereignty-first system. This repository is its English-language
home: the long-term goals, the governance principles we bind ourselves to, and — as
they are cleared for release — the specifications and modules that implement them.

English is the authoritative language of this repository. If a translation conflicts
with the text here, this text governs.

---

## Status of this document

These are **commitments**, not a claim of completed guarantees.

We publish principles before implementation on purpose, so that the gap between the two
is visible and arguable. Where a guarantee is not yet implemented, measured, or
independently verified, we say so explicitly instead of implying it. A principle in this
repository is a promise about direction and about what we are forbidden to claim — not a
certification of the current code.

See [PRINCIPLES.md](PRINCIPLES.md) for the numbered principles, the reasoning behind
each one, and the tests a reviewer can apply to check whether we are keeping them.

---

## 1. Payment data is minimized, and payment is isolated from user content

- LongHun itself should receive **only the minimum credentials required to verify
  entitlement to a participation right** — nothing more.
- The payment module must be **isolated from user content**. What a person pays for, and
  what a person writes, stores, or reads, are separate domains.
- We must **not claim that payment is "zero personal data end to end."** A payment
  channel necessarily touches third parties (banks, processors, networks) that we do not
  control. Claiming otherwise would be false comfort, and false comfort in this area is
  worse than an honest limitation.

## 2. Payment is not proof of a human being

- A **paid participation or support credential is evidence of support. It is not evidence
  of a person.** It cannot, on its own, establish that a unique human being is behind an
  account.
- **Personhood verification must be designed separately.** Where it is needed, it must
  prioritize privacy protection, resistance to Sybil attacks, and a real path to appeal.
- **Biometric collection is not a default.** It is not the first answer, and it is never
  a silent condition of participation.

## 3. Sovereignty principles

**No back-end sovereignty.**
Entry points may be unified; power may not be centralized. Tools may interconnect; user
data and control must not be taken away. Convenience is never a justification for a
backend that can read, move, or monetize what users did not hand over.

**The same rules for everyone.**
Ordinary users, developers, and governance participants are bound by the same rules.
Contribution can be seen and credited. **Wealth cannot buy privilege** — not in access,
not in review, not in enforcement.

**Open-source co-supervision.**
The community reviews in public. Decisions are open to challenge, open to appeal, and
open to revocation. A rule that cannot be appealed is not governance; it is a leash.

---

## Long-term goals

1. **Data stays with the person it belongs to.** Portability and exit are first-class
   features, not favors granted on request.
2. **Transparency that can be checked by an outsider.** Every stage that could change
   meaning leaves a verifiable trace — not a summary written by the same system that is
   being audited.
3. **Governance that survives its own operators.** Power is separated, revocable, and
   cannot be inherited by whoever happens to hold the servers.
4. **Participation that is open, and support that is honest.** Support is acknowledged as
   support. It is never quietly converted into authority, identity, or immunity.
5. **Evidence over claims.** An unverifiable statement is labeled unverified. Green check
   marks are earned by artifacts, not by confidence.

---

## What this repository forbids us to claim

| We will not claim | Because |
|:--|:--|
| "Payments involve zero personal data." | Third-party processors and networks are outside our control. |
| "Payment proves a real human." | Payment is evidence of support, not of personhood. |
| "Fully decentralized." | If a backend exists and holds power, the system is not decentralized, however it is marketed. |
| "Audited," when no independent audit exists. | Self-review is not independent review. |
| "Verified," when the evidence has not been produced. | Verification is an artifact, not an adjective. |

---

## Maintainer and legal entity

This project is maintained by its author and steward, and published under the following
legal entity:

| Item | Value |
|:--|:--|
| Legal name (Chinese) | 瑞安市熵梦科技有限公司 |
| Legal name (English) | Ruian Shimeng Technology Co., Ltd. |
| Unified Social Credit Code | `91330381MAKM62CM8C` |
| Legal representative | Zhuge Xin (诸葛鑫) |
| Entity type | Limited liability company (wholly owned by a natural person) |
| Established | 2 September 2026 |
| Registration authority | Ruian Municipal Market Supervision Administration |
| Registered location | Ruian, Wenzhou, Zhejiang, China *(street address withheld for privacy)* |
| Business scope (summary) | Software development; artificial-intelligence application software; network and information-security software; blockchain-related software and services; technical development, consulting, transfer and promotion; software outsourcing and sales |
| Public contact | uid9622@petalmail.com |

The Unified Social Credit Code is a public registry identifier. Personal contact details
of individuals are deliberately not published here.

---

## Licensing

- **Prose and principles** in this repository: CC BY-NC-SA 4.0 — share and adapt with
  attribution, non-commercial, under the same terms.
- **Code modules**, when published here: MulanPSL v2 (Mulan Permissive Software License,
  version 2), the license already used by LongHun engineering repositories.

This repository currently contains documents only, so only the document license applies
so far. Each future source directory will carry its own license file; nothing here should
be read as relicensing code that lives elsewhere.

---

## Contributing and review

- Discussion and review happen in public, in issues and pull requests.
- Contribution is credited by artifact and traceable record, not by rank.
- Objections are answered on the record. Decisions can be appealed and can be revoked.
- Reports that a published claim is false or unverifiable take priority over new features.

---

## Contact

- Email: uid9622@petalmail.com
- Issue tracker: this repository

If something in this repository overstates what the system does, that is a defect. Please
report it as one.

<!-- DNA: #龍芯⚡️丙午·己亥·己丑·壬申·䷉履-文档-创建-959103f7 -->
