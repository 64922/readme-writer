# 样例分析：学什么、不学什么

4 份参考样例（均为产品/框架类项目）：

| 样例 | 行数 | 流派 |
|------|------|------|
| [AI-Researcher](https://github.com/HKUDS/AI-Researcher/blob/main/README.md) | ~1100 | 产品秀：重度视觉 + 超长用例 |
| [DeepTutor](https://github.com/HKUDS/DeepTutor/blob/main/README.md) | ~1160 | 产品秀：12 语 switcher + 可折叠 changelog |
| [LightRAG](https://github.com/HKUDS/LightRAG/blob/main/README.md) | ~680 | 产品秀：居中 hero + 多语言 |
| [llama-index](https://github.com/run-llama/llama_index/blob/main/README.md) | ~220 | 极简框架：诚实定位 + 全部外链 docs |

## 共同骨架（学）

1. 居中 hero：logo → 名称 → 一句话定位 → 真实 badge 行 → 锚点导航/语言切换（DeepTutor）
2. badge 全部真实：CI、包版本、下载量、License、社区入口，一一指向真实目标
3. 首屏附近放真实截图/架构图（LightRAG 的 GIF + 架构图）
4. Quick Start 命令可复制、多路径安装（pip / 源码 / Docker）
5. 长内容折叠：DeepTutor 的 Releases / 历史版本用 `<details>`
6. 学术项目带 Citation（对应真实论文）；更新记录对应真实 release
7. llama-index 的诚实 NOTE：不吹大、说清定位现状——"诚实边界"的样板

## 反例（不学）

1. AI-Researcher 把 7 个用例 ~700 行全塞 README → 违反篇幅预算，应拆 docs 或折叠
2. 渐变 div、复杂内联 style → 跨渲染器易碎，属过度装饰
3. 12 语 switcher：维护成本高、易过期——除非用户真在维护，否则不主动加
4. 装饰性/虚假 badge（只求好看、不指向真实状态）→ 禁止
5. 无实据的空洞营销词（revolutionary、state-of-the-art）→ 禁止

## 各样例结构速查

### AI-Researcher

hero（logo + 两行 badge）→ 价值点 bullets → `## News` → `## Table of Contents` → `## Quick Start`（Installation / API Keys / Web GUI）→ `## Examples` ×7（约 700 行，反例）→ `## How it works` → `## How to use` → `## Documentation` → `## Community` → `## Misc` → `## Cite`

### DeepTutor

hero（logo + banner + 12 语 switcher + 堆叠 badge + 锚点导航）→ Contributing callout → Releases（`<details>` 历史）→ News → Key Features → Get Started（Docker / venv / CLI 多路径，约 400 行）→ Explore（截图深潜）→ CLI 节 → Ecosystem → Partners → Community

### LightRAG

hero（logo + star-history + 语言行 + 下载 badge）→ GIF / 架构图 → 合作方 banner → News → Installation（多路径约 140 行）→ About → Key Configuration → SDK 用法 → 复现论文 → Docs 索引 → Related Projects → Contribution → Citation

### llama-index

H1 + badge 行 → 诚实 NOTE（定位变化）→ 是什么 + 两种起步方式 → 代码示例 → LlamaParse 节 → Important Links → Overview（Context → Solution）→ Contributing → Documentation → Example Usage → 构建资产验证说明 → Citation
