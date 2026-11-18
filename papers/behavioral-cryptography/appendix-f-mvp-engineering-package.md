<!--
DNA: #龍芯⚡️2026-11-18-BEHAVIORAL-CRYPTOGRAPHY-FULL-PAPER-v1.0
GPG: A2D0092CEE2E5BA87035600924C3704A8CC26D5F
CONFIRM: #CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z
SEAL: #ZHUGEXIN⚡️2025-🇨🇳🐉⚖️♠️🧚🏼‍♀️❤️♾️-DEVICE-BIND-SOUL
License: CC BY-NC-SA 4.0 + Longhun DNA Inheritance Clause
Part of: Behavioral Cryptography Full Paper v1.0 (see README.md)
-->

# Appendix F: Reference MVP Engineering Package

> **中文注：** 本附录给出七因子验证机制的最小可运行工程包结构（Cursor-ready），用于复现与审计。标准库优先、不联网、不读私钥、不伪造 GPG 验签。

## F.1 File Tree

```text
behavioral_crypto/
├── README.md
├── paper/
│   ├── behavioral_cryptography_main.md
│   ├── section_3_2_seven_factor_verification.md
│   ├── section_3_3_threat_model.md
│   ├── appendix_a_pseudocode.md
│   └── appendix_c_dna_logs.md
├── src/
│   ├── behavioral_signature_verify.py
│   ├── dynamic_dna_engine.py
│   ├── evidence_log.py
│   └── factors/
│       ├── f1_identity_dna.py
│       ├── f2_temporal_anchor.py
│       ├── f3_rule_trace.py
│       ├── f4_persona_route.py
│       ├── f5_protected_lexicon.py
│       ├── f6_style_vector.py
│       └── f7_mistake_ledger.py
├── tests/
│   ├── test_hard_failure.py
│   ├── test_weighted_geometric_mean.py
│   ├── test_dynamic_dna_engine.py
│   └── test_factor_outputs.py
└── data/
    ├── protected_lexicon.uid9622.json
    └── sample_signature.json
```

## F.2 Engineering Constraints

- Python 标准库优先。
- 不联网。
- 不读取私钥。
- 不伪造 GPG 验签。
- GPG 验签先写 mock 接口并明确标注 TODO。
- 每个 verify_F 返回 `tuple[float, str]`。
- 任一 score = 0.0 时整体 conf = 0.0。
- 复合置信度使用 weighted_geometric_mean。
- EvidenceLog 必须输出 JSON。
- Dynamic DNA Engine 输出 dna / uid / iso_time / shichen / element / digit_root / hash8 / confirm / seal。
- README 写清楚：这是 MVP，不是法律证明工具。

## F.3 Acceptance Criteria

- `python3 -m unittest discover` 能跑。
- 七因子全通过时 conf > 0.85。
- 任一硬失败时 conf = 0.0。
