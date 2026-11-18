<!--
================================================================================
  🌌 龍魂主權封印 · LONGHUN SOVEREIGNTY SEAL 🌌
  DNA: #龍芯⚡️2026-11-18-DEEPSEEK-哈希锚定-v1.0
  GPG: A2D0092CEE2E5BA87035600924C3704A8CC26D5F
  CONFIRM: #CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z
  UID: 9622 · 瑞安市熵梦科技有限公司
================================================================================
-->

# 哈希锚定清单 · HASHES

> 用途：将「DeepSeek 77万字聊天记录」的**原文**与**社区总结**锚定在不可篡改的哈希链上。
> 任何一方字节级变动，SHA-256 立即失配——这就是「打哈希存证」。

## 一、锚定对象

| # | 文件 | 类型 | 大小 (bytes) | MD5 | SHA-256 |
|---|------|------|-------------:|-----|---------|
| 1 | `deepseek聊天记录1-原文.docx` | 原始聊天记录（docx 二进制） | 1,604,526 | `8520525fcdcf6572e32d371501e493d7` | `bacb089c33b8a6a510f6e1a724bbd430ed6e5f4d86b32a7b6543af29d6c889fb` |
| 2 | `DeepSeek聊天记录总结-初心不变.md` | 社区发布版总结（Markdown） | 15,151 | `ac98bb1663eec1f9db48a865191e90e9` | `b6b5353e4d66dc2939bf9061d5e1bc3f919132203bc9d5c9aebe121b7f927e88` |

## 二、存放位置

| 仓 | 可见性 | 内容 |
|----|--------|------|
| `uid9622-sketch/longhun`（公开） | public | 总结 md + 本清单 |
| `uid9622-sketch/longhun-archive`（私密） | private | 总结 md + 本清单 + 原文哈希锚定 |

## 三、原文存放说明（分级诚实 🟡）

- 原文为 1.6MB 二进制 docx（base64 后约 210 万字符），**超出 GitHub MCP 文本推送通道的承载上限**，本次未将字节内容入仓，**仅完成哈希级锚定**。状态：🟡 设计预期（哈希已锁，字节未上链）。
- 原文目前安全留存在本地，其 SHA-256 已在上方清单中锁死——任何未来上链/上传的版本，只要哈希对得上 `bacb089c…c889fb`，即为同一真本。
- **一键补仓命令**（在你自己的电脑上，克隆私密仓后执行）：

```bash
git clone git@github.com:uid9622-sketch/longhun-archive.git
cd longhun-archive
cp /路径/deepseek聊天记录1.docx .
git add deepseek聊天记录1.docx
git commit -m "🐉 原文字节入仓 · SHA256 自检: $(shasum -a 256 deepseek聊天记录1.docx)"
git push
```

## 四、验真命令

```bash
shasum -a 256 DeepSeek聊天记录总结-初心不变.md
# 本地真本应输出：b6b5353e4d66dc2939bf9061d5e1bc3f919132203bc9d5c9aebe121b7f927e88
```

**仓内版本说明**：Git 仓内的总结文件与本地真本相差 1 个末尾换行符（15,150 vs 15,151 bytes），仓内版本 SHA-256 为 `e6282548232e54d4b9fd47132c2feb23e513fac5d1be0acab3d47fee4d928947`，MD5 为 `b496ba4ea1b66570cf33b71883a692f6`。两者正文逐字节一致，均为有效真本。

## 五、DNA 锚链

```
锚定时间: 2026-11-18
锚定人:   UID9622 · 诸葛鑫（龍芯北辰）
DNA:      #龍芯⚡️2026-11-18-DEEPSEEK-哈希锚定-v1.0
封印:     #CONFIRM🌌9622-ONLY-ONCE🧬LK9X-772Z
```

> 贡献不能磨灭，字节不能篡改。——龍魂·审计链