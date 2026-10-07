# 样例与语料库：学什么、不学什么

## 第一部分：4 份深度样例（产品 / 框架类）

| 样例 | 行数 | 流派 |
|------|------|------|
| [AI-Researcher](https://github.com/HKUDS/AI-Researcher/blob/main/README.md) | ~1100 | 产品秀：重度视觉 + 超长用例 |
| [DeepTutor](https://github.com/HKUDS/DeepTutor/blob/main/README.md) | ~1160 | 产品秀：12 语 switcher + 可折叠 changelog |
| [LightRAG](https://github.com/HKUDS/LightRAG/blob/main/README.md) | ~680 | 产品秀：居中 hero + 多语言 |
| [llama-index](https://github.com/run-llama/llama_index/blob/main/README.md) | ~220 | 极简框架：诚实定位 + 全部外链 docs |

### 共同骨架（学）

1. 居中 hero：logo → 名称 → 一句话定位 → 真实 badge 行 → 锚点导航/语言切换（DeepTutor）
2. badge 全部真实：CI、包版本、下载量、License、社区入口，一一指向真实目标
3. 首屏附近放真实截图/架构图（LightRAG 的 GIF + 架构图）
4. Quick Start 命令可复制、多路径安装（pip / 源码 / Docker）
5. 长内容折叠：DeepTutor 的 Releases / 历史版本用 `<details>`
6. 学术项目带 Citation（对应真实论文）；更新记录对应真实 release
7. llama-index 的诚实 NOTE：不吹大、说清定位现状——"诚实边界"的样板

### 反例（不学）

1. AI-Researcher 把 7 个用例 ~700 行全塞 README → 违反篇幅预算，应拆 docs 或折叠
2. 渐变 div、复杂内联 style → 跨渲染器易碎，属过度装饰
3. 12 语 switcher：维护成本高、易过期——除非用户真在维护，否则不主动加
4. 装饰性/虚假 badge（只求好看、不指向真实状态）→ 禁止
5. 无实据的空洞营销词（revolutionary、state-of-the-art）→ 禁止

### 各样例结构速查

#### AI-Researcher

hero（logo + 两行 badge）→ 价值点 bullets → `## News` → `## Table of Contents` → `## Quick Start`（Installation / API Keys / Web GUI）→ `## Examples` ×7（约 700 行，反例）→ `## How it works` → `## How to use` → `## Documentation` → `## Community` → `## Misc` → `## Cite`

#### DeepTutor

hero（logo + banner + 12 语 switcher + 堆叠 badge + 锚点导航）→ Contributing callout → Releases（`<details>` 历史）→ News → Key Features → Get Started（Docker / venv / CLI 多路径，约 400 行）→ Explore（截图深潜）→ CLI 节 → Ecosystem → Partners → Community

#### LightRAG

hero（logo + star-history + 语言行 + 下载 badge）→ GIF / 架构图 → 合作方 banner → News → Installation（多路径约 140 行）→ About → Key Configuration → SDK 用法 → 复现论文 → Docs 索引 → Related Projects → Contribution → Citation

#### llama-index

H1 + badge 行 → 诚实 NOTE（定位变化）→ 是什么 + 两种起步方式 → 代码示例 → LlamaParse 节 → Important Links → Overview（Context → Solution）→ Contributing → Documentation → Example Usage → 构建资产验证说明 → Citation

## 第二部分：121 份语料库抽样结论（2026-10 实测）

方法：从 awesome-readme 清单批量下载 121/128 份 README（7 份不可达，跳过），机器统计结构特征 + 逐份人工精读，并与 Standard Readme / READMINE / readme-best-practices 等规范类文本交叉验证。

### 量化底数

- 行数：中位 210，最短 28，最长 1158——中位数正好落在 150–400 预算内；>700 行的多是反例。
- 节频率：安装 / 上手 55%、License 50%、Contributing 45%、Usage 42%、Features 33%、Why 25%、Community 25%、ToC 24%、Acknowledgements 23%、Roadmap 12%。
- 手法统计：平均每份 16 张图、12 行表格；`<details>` 约每 4 份出现 1 次；居中 hero 是产品类标配。

### 高频有效模式（跨批次反复出现）

1. 首屏演示（GIF / 截图 / 视频 / 基准图）——约六成文件；"一眼信服"的最强手段
2. 诚实声明局限、未验证项与上线边界——最高辨识度的可信度来源
3. 信息表格化：安装路径、参数（类型/默认/必填）、兼容矩阵、安全边界、对比
4. `<details>` 折叠长内容（changelog / ToC / 长示例 / 安装变体）
5. "为什么选我"对比表，或先讲替代品缺陷再给方案
6. 安装路径场景化（"如果你是 A 用 B"）与多平台分流
7. 预期输出 / 可自查证据（终端横幅、`--help` 输出、截图）
8. ToC + "回到顶部"链接（长文）
9. Demo / Showcase 直达链接；功能点配 live demo
10. Acknowledgements / Prior art：灵感来源、第三方资产与许可

### 独特手法精选（值得记住的样板）

- **Terminal.Gui**：hero 动图的 alt 写成完整卖点摘要——无障碍与可检索双赢
- **vhs**：README 演示 GIF 由项目自身生成并链接 `.tape` 源码——演示即产物，可复现
- **dvc**：把端到端工作流压成"任务 → 终端命令"表，再用类比定位（Git for data）
- **bia-bob**：AI 工具列明"发给 LLM 的数据清单"+ verbose 自查开关
- **Bridge**：安全模型做成"场景 × 可达面"矩阵；Roadmap 勾选式分"已完成 / 计划中"
- **QuickSwitch**：未验证安装法整段显式标注（UNDER VERIFICATION）——可信度分层
- **httpie**：正文公开事故复盘（曾误设私有丢失 54k star）——透明反营销
- **radioactive-state**：折叠块 `<summary>` 内直接放 GIF，展开前先见效果
- **ohmyzsh**：安装表标注镜像可用性 + 建议先审安装脚本——供应链安全
- **nerd-fonts**：9 种安装法各配 "Best option if…" 决策句，按场景分流
- **dec0dOS / implot3d**：Roadmap 链到实时 issue 查询或自动生成图，永不腐坏

### 语料库反模式汇总（禁止）

1. badge 墙 / 求 star / 赞助与 affiliate 靠前 / 自证维护 badge / 假 badge（如 npm 自指）/ 死服务 badge（Travis）
2. 空章节与占位残留（TODO、NEED TO ADD IMAGE、link needed）
3. 空洞营销词（powerful、revolutionary）与过度卖萌
4. 超长内容不折叠（changelog、API 清单、设备清单）；README 写成 docs
5. 彩虹分隔线、emoji 过量、装饰性 HTML 花活
6. 难维护的翻译墙（12 语 switcher 无人维护）
7. 开源库 README 夹带商业价目表；私人信息进入正文
8. 自夸"入选 awesome 清单"类 badge
