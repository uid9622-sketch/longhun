# LongHun Principles

Version 1.0 — 11 November 2026

Each principle below has three parts: the **rule**, the **reason**, and a **test** — a way
for an outside reviewer to check whether the rule is actually being kept. Where a rule
forbids a claim, that is stated as a **non-claim**, because most of the harm in this field
is done by true-sounding sentences that nobody was allowed to check.

These principles apply equally to ordinary users, developers, and governance
participants. They are written to bind the operators of LongHun, not to decorate it.

---

## A. Payment, data minimization, and personhood

### P-01 — Minimum credentials only

**Rule.** LongHun itself should receive only the minimum credentials required to verify
entitlement to a participation right.

**Reason.** Any field we do not need is a field we can leak, subpoena, resell, or
misread later. Data we never collect cannot be abused.

**Test.** For each stored field on a payment or entitlement path, a maintainer must be
able to name the specific decision that field enables and the rule that requires it. If
the answer is "maybe useful later," the field does not belong on the path.

**Non-claim.** We do not claim that third-party payment channels are minimal. We control
what LongHun receives, not what a bank or processor keeps.

### P-02 — Payment is isolated from user content

**Rule.** The payment module must be isolated from user content.

**Reason.** Billing asks "is this entitled?" Content asks "what does this person think,
write, or keep?" Letting those two touch converts a billing system into a surveillance
system with a receipt printer attached.

**Test.** Trace the data flow. User content must not be readable from the payment module,
and payment records must not be joinable to content by the payment module itself. Any
shared identifier that makes the join trivial is a violation, even if nobody performs the
join today.

### P-03 — No "zero personal data" claim for payments

**Rule.** We must not claim that payment involves zero personal data throughout.

**Reason.** A payment touches banks, processors, card networks, and telecom infrastructure.
Everyone in that chain sees something. A "zero data" claim is not privacy; it is
marketing that teaches users to stop asking questions.

**Test.** Any public statement about payment privacy is checked against the actual
processor list. If the statement cannot survive reading the processor's own privacy
policy, it must be rewritten or withdrawn.

**Non-claim.** We claim only: minimized collection by LongHun, isolation from content, and
a stated retention limit.

### P-04 — Payment is not proof of personhood

**Rule.** A paid participation or support credential is evidence of support. On its own it
cannot establish that a unique human being is behind an account.

**Reason.** Money is transferable. Identity is not. Treating payment as a humanity test
converts "who can pay" into "who counts," which is both a Sybil hole and a fairness
failure.

**Test.** Read any access rule that depends on a payment record. Ask: could one determined
person with funds satisfy it many times over? If yes, the rule is an entitlement rule and
must not be labeled an identity rule.

### P-05 — Personhood verification is separate, private, appealable, non-biometric by default

**Rule.** Where personhood verification is required, it must be designed as a separate
mechanism that prioritizes privacy protection, resistance to Sybil attacks, and a real
path to appeal. Biometric collection is not a default.

**Reason.** A personhood gate that cannot be appealed becomes an exclusion machine. A
personhood gate that collects biometrics by default creates a permanent, unchangeable
identifier — the most dangerous artifact such a system can hold.

**Test.** For any such mechanism, an operator must be able to show: (a) what is stored and
for how long, (b) how a false negative is contested and by whom, (c) what happens to a
person who declines the biometric path. If (c) is "no participation," the default is
biometric in practice.

---

## B. Sovereignty

### P-06 — No back-end sovereignty

**Rule.** Entry points may be unified. Power may not be centralized. Tools may
interconnect. User data and control must not be taken away.

**Reason.** A single front door is convenience. A single back door is sovereignty
transfer. The difference is not architectural fashion; it is who can say no, and who
cannot be made to.

**Test.** Identify every component that can read or move user data without the user's
action. For each one, ask what stops it, and who that stopper answers to. "Our good
intentions" is not a control.

**Non-claim.** As long as a backend exists that holds such power, we do not describe the
system as decentralized, federated, or trustless.

### P-07 — The same rules for everyone

**Rule.** Ordinary users, developers, and governance participants follow the same rules.

**Reason.** A system with two rulebooks has one rulebook: the one the powerful use.

**Test.** Compare the enforcement path for a maintainer and for a new user who commits the
same violation. If the paths differ in outcome, the difference must be justified in
writing and open to appeal.

### P-08 — Contribution is visible; wealth buys no privilege

**Rule.** Contribution can be seen and credited. Wealth cannot purchase privilege — not
access, not review weight, not enforcement leniency.

**Reason.** Support is legitimate and should be acknowledged. But once money converts to
authority, governance becomes an auction, and the people who most need protection become
the least able to afford it.

**Test.** Every governance action must name the role or mandate it exercises. No action may
be justified by the size of a contribution. Payment records must never appear as an input
to a governance decision.

### P-09 — Open co-supervision

**Rule.** The community reviews in public. Decisions are open to challenge, open to appeal,
and open to revocation.

**Reason.** Review that cannot be seen is not review. Authority that cannot be withdrawn is
not delegated.

**Test.** For any decision, an outsider must be able to locate: the rule applied, the
evidence considered, who decided, and the route to appeal. If any of those four is missing,
the decision is not yet governable.

---

## C. Evidence

### P-10 — Evidence over claims

**Rule.** Unverifiable statements are labeled unverified. Every stage that could change
meaning leaves a trace an outsider can check.

**Reason.** The cheapest way to fail at transparency is to publish a confident summary
produced by the same system being audited. Confidence is not evidence; a self-written
summary is not an audit.

**Test.** Pick any published guarantee. Ask who could disprove it, with what artifact, and
whether that artifact exists today. If nobody could, or the artifact does not exist, the
guarantee must be downgraded to intent.

**Non-claim.** We do not use the words audited, certified, or verified for work that has
not been independently checked. Where our own review found a defect, we publish the defect,
not only the fix.

---

## Enforcement of these principles on ourselves

1. A published statement that overstates what the system does is treated as a defect, with
   the same priority as a functional bug.
2. A principle that cannot be tested is rewritten until it can be, or removed. Untestable
   virtue is decoration.
3. These principles bind the maintainers first. If a principle is inconvenient for us, that
   is the case it was written for.

---

*LongHun — 龍魂 · Ruian Shimeng Technology Co., Ltd. · uid9622@petalmail.com*

<!-- DNA: #龍芯⚡️丙午·己亥·己丑·壬申·䷉履-文档-创建-9fad1199 -->
