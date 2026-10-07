---
name: readme-writer
description: 为软件项目撰写或改进 README.md（真实第一：声明可溯源）。触发：写/生成 README、"这个仓库缺个 README"、项目介绍文档；改进/重写/审计 README、"README 写得不好"。反触发：非软件仓库（awesome list、数据集、纯文档站）；README.md 以外的文件（CHANGELOG、CONTRIBUTING、API 文档）；纯代码任务。
argument-hint: "仓库路径（默认当前目录），可附加读者/语气等侧重"
---

# Skill: readme-writer

为软件项目撰写或改进 `README.md`。

## 铁律

1. **真实第一**：每条声明、每个数字、每个链接必须可回溯到仓库事实或用户明示。查不到就删、降级或标注"待确认"。禁止编造功能、badge、benchmark。
2. **只碰 README.md**：不创建/修改其他文件。缺失的 LICENSE/CONTRIBUTING 等只在收尾报告里提示，不代建。
3. **事实自己查，决策问用户**：能从仓库查到的绝不问人；定位、取舍、语气由用户拍板。
4. **缺素材宁可省略**：任何节缺证据就省略或降级为一句，禁止空壳节。
5. **首屏优先**：读者在前 40 行内能回答"是什么、给谁、凭什么选它"；有真实演示（GIF / 截图 / 在线 Demo）就优先于长文案；长内容折叠或外链，不堆在主干上。
6. **未核实不得声称完成**：自检有缺口时如实报告剩余待确认项。

## 工作流

### 阶段 1 取证（自动）

先读 `references/templates.md` 掌握骨架，读 `references/samples.md` 了解样例的学/不学与语料库结论。

- 判断模式：有 `README.md` → 改进模式；无 → 生成模式。
- 扫描仓库：manifest（package.json / pyproject.toml / Cargo.toml / go.mod 等，含 scripts 与入口）、目录结构与项目类型（库 / CLI / 服务 / 应用，类型决定骨架侧重）、可运行线索（Makefile、docker-compose、CI）、现有文档（docs/、CONTRIBUTING、LICENSE、CHANGELOG）、已有翻译文件（README-zh.md 等）、git remote 与 log（组织、活跃度、停更线索）。
- 盘点演示与佐证素材：assets 中的截图 / GIF / 视频、在线 Demo、release 页（News 素材）、issue 区（FAQ 与 Roadmap 素材）。
- 改进模式：逐节诊断已有 README，产出"保留 / 重写 / 删除 / 新增"清单。
- 超小项目（单文件、核心代码 <500 行）：允许裁剪为最小节集合（名称+一句话 / 用法 / 许可），不硬凑章节。
- Monorepo：默认只处理根 README；用户明确指定子包才处理该子包。

**完成标志**：模式已判定；凡仓库能查到的信息都已取证，查不到的列成阶段 2 访谈清单。

### 阶段 2 补缺访谈（只问查不到的）

成组提问，附上你的推断让用户确认，而非从零回答：

1. 目标读者与主使用场景（新用户 / 贡献者 / 集成方）？
2. 与哪些替代品对比、差异一句话？（直接支撑定位句与对比表）
3. 成熟度承诺（alpha / beta / 稳定 / 停更）与已知限制、未验证事项？
4. 真实演示素材（GIF / 截图 / 视频 / 在线 Demo）与社区入口？
5. 可选节取舍（News / FAQ / Roadmap / Demo / Architecture / Ecosystem / Community / Citation / 语言 switcher / ToC / AI 工具节）？

答不上来的记"待确认"。语言：改进模式默认保持原语言；生成模式依据仓库信号提议一种主语言并由用户确认。

**完成标志**：写作所需的信息全部已确认或标为"待确认"。

### 阶段 3 大纲 gate

输出：章节大纲（核心节 + 选中的可选节）、首屏安排（定位句、演示、badge）、折叠策略（哪些内容进 `<details>`、哪些外链 docs）、每节要点、保留/重写清单（改进模式）、素材缺口。
**完成标志：用户明确批准大纲与清单；批准前不得动笔。**

### 阶段 4 成稿

按 `references/templates.md` 各节规范写作，遵守篇幅预算（首屏 ≤40 行；正文 150–400 行；>500 行逐节自问"这内容属于 README 还是 docs"）。

三条读者路径是成稿标尺：**3 秒**（首屏说清是什么 / 给谁 / 凭什么）、**60 秒**（Quick Start 四件套可跑通且知道成功的样子）、**5 分钟**（对比、局限、演示、深入链接足以决策）。

写入规则：直接写 `README.md`；覆盖已有文件且非 git 仓库时，先把原文件备份到系统临时目录（备份路径写进报告）；git 仓库靠 `git diff` 兜底。全程只碰 README.md。

**完成标志**：`README.md` 已写出，篇幅与三路径要求达标。

### 阶段 5 自检

按 `references/verification.md` 执行六条回验（含读者三路径走查），产出核对报告：读者路径结论 + 已核实 / 待确认 / 缺失提示 / 备份路径。

**完成标志**：六条回验各有结论，报告五段齐全。

## 反触发

- 非软件仓库（awesome list、数据集、纯文档站）→ 说明 genre 不同后拒绝，不硬套软件骨架。
- 请求创建/修改 README.md 以外的文件 → 拒绝并说明。

## References

| 文件 | 内容 |
|------|------|
| `references/templates.md` | 骨架、各节规范、Hero HTML 最小集、badge 白名单、表达工具选择、篇幅预算 |
| `references/verification.md` | 六条回验的执行细则与报告格式 |
| `references/samples.md` | 4 份样例精析 + 121 份语料库统计、高频模式与反例清单 |
