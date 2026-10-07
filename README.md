# readme-writer

为软件项目撰写与改进 `README.md` 的 Agent Skill——**真实第一**：每条声明可回溯，查不到就省略，动笔前先过你的大纲确认。

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)

## 这是什么

`readme-writer` 面向 Claude Code、opencode 等 AI 编程 Agent。当你说"给这个仓库写个 README"，它不会让模型自由发挥，而是：

- 先**扫描仓库事实**（manifest、入口、CI、git 历史、现有文档），能从代码里查到的绝不问你
- 只对查不到的信息**成组提问**（目标读者、差异点、成熟度、可选节取舍）
- 先给出**大纲与保留/重写清单**，你批准后才动笔
- 写完后**逐条回验**命令、链接、数字与声明，产出核对报告

与"一键生成 README"的差异：它把真实性当铁律——查不到的宁可省略，也不编造功能、badge 或 benchmark。

### 核心规则（全部来自技能文件）

- **双模式**：已有 README → 先诊断"保留/重写/删除/新增"；没有 → 从零生成
- **五阶段工作流**：取证 → 补缺访谈 → 大纲 gate → 成稿 → 自检
- **三条读者路径**：3 秒看懂首屏（是什么/给谁/凭什么）、60 秒跑通 Quick Start、5 分钟凭对比与演示做出决策
- **六条回验**：声明溯源、命令静态核对、链接与媒体核对、数字核对、读者三路径走查、核对报告——存在未核实项时不声称完成
- **结构规范**：核心 7 节 + 证据门控的可选节（News、FAQ、Roadmap、Demo、Citation 等有真实素材才加）；缺素材省略或降级，禁止空壳
- **只碰 README.md**：不代建 LICENSE、CONTRIBUTING 等，缺失只在收尾报告提示
- **篇幅纪律**：首屏 ≤40 行、正文 150–400 行；超过 500 行触发逐节审查

### 诚实边界

- 初始版本：规则基于 [awesome-readme](https://github.com/matiassingers/awesome-readme) 语料库（121 份）系统性优化过一轮，仍在试跑验收，可能随实践调整
- 需要支持 Agent Skills 的运行时（Claude Code、opencode 等共享 SKILL.md 格式）
- 只面向软件项目：awesome list、数据集、纯文档站不适用
- 只交付 README.md 一个文件

## 规则从哪来：awesome-readme 语料库

本 Skill 的核心规则并非拍脑袋写成，而是从 [**awesome-readme**](https://github.com/matiassingers/awesome-readme/tree/master)（社区公认的优质 README 收藏仓库）系统性提炼而来：

- 批量下载清单中的 **121 份** README（共 128 个仓库，7 份不可达），机器统计结构特征 + 逐份人工精读
- 由此提炼出三条读者路径（3 秒 / 60 秒 / 5 分钟）、六条回验、首屏演示优先、`<details>` 折叠边界、表格适用场景、13 个证据门控可选节等规则
- 并用其中 4 份不同形态的 README 做了反向验收（sniffnet、edlib、voltagent、Reaparr）
- 语料库的量化底数、高频模式、独特手法与反例清单沉淀在 [`readme-writer/references/samples.md`](readme-writer/references/samples.md)

感谢 [Matias Singers](https://github.com/matiassingers) 与所有被收录项目的维护者——这份清单是本次规则迭代最重要的灵感与证据来源。

## 快速开始

前置：一个支持 Agent Skills 的运行时（如 Claude Code、opencode）。

```bash
git clone https://github.com/64922/readme-writer.git
```

安装到用户级技能目录（对所有项目生效）：

```powershell
# Windows PowerShell
Copy-Item -Recurse .\readme-writer\readme-writer "$env:USERPROFILE\.agents\skills\"
```

```bash
# macOS / Linux
cp -r readme-writer/readme-writer ~/.agents/skills/
```

放进项目的 `.agents/skills/` 则只对该项目生效。

使用——直接对 agent 说：

> 给这个仓库写一份 README，读者是 Python 开发者。

预期输出：

1. 大纲（含保留/重写清单与素材缺口），经你确认后动笔
2. `README.md`
3. 核对报告：已核实 / 待确认 / 缺失提示 / 备份路径

## 改进已有 README

对一份过时的 README 说"改进这个"：

1. 技能先诊断现状，产出保留/重写/删除/新增清单与大纲，**等你批准**（gate）
2. 批准后改写，全程只碰 `README.md`；非 git 仓库会先把原文件备份到系统临时目录
3. 收尾给出核对报告：哪些已核实、哪些基于你的口述标记"待确认"、是否缺少 LICENSE 等

## 深入阅读

| 文件 | 内容 |
|------|------|
| [`readme-writer/SKILL.md`](readme-writer/SKILL.md) | 工作流、铁律、反触发 |
| [`readme-writer/references/templates.md`](readme-writer/references/templates.md) | 骨架、各节规范、badge 白名单、表达工具选择、篇幅预算 |
| [`readme-writer/references/verification.md`](readme-writer/references/verification.md) | 六条回验执行细则与报告格式 |
| [`readme-writer/references/samples.md`](readme-writer/references/samples.md) | 4 份样例精析 + 121 份语料库统计、高频模式与反例清单 |

## 贡献

欢迎提 issue 或 PR。

## License

[MIT](./LICENSE) © 2026 idiotGu
