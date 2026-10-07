---
name: readme-writer
description: 为软件项目撰写或改进优质的 README.md，含诊断、取证、访谈、成稿与真实性自检。触发场景：写 README、生成/改进/审计/重写 README、项目介绍文档、"这个仓库缺个 README"、"README 写得不好"。反触发：不负责 CHANGELOG/CONTRIBUTING/LICENSE/API 文档，不接纯代码任务，不适用于非软件仓库（awesome list、数据集、纯文档站）。
argument-hint: "仓库路径（默认当前目录），可附加读者/语气等侧重"
---

# Skill: readme-writer

为软件项目撰写或改进 `README.md`。**全程只交付这一个文件。**

## 铁律

1. **真实第一**：每条声明、每个数字、每个链接必须可回溯到仓库事实或用户明示。查不到就删、降级或标注"待确认"。禁止编造功能、badge、benchmark。
2. **只碰 README.md**：不创建/修改其他文件。缺失的 LICENSE/CONTRIBUTING 等只在收尾报告里提示，不代建。
3. **事实自己查，决策问用户**：能从仓库查到的绝不问人；定位、取舍、语气由用户拍板。
4. **缺素材宁可省略**：任何节缺证据就省略或降级为一句，禁止空壳节。
5. **未核实不得声称完成**：自检有缺口时如实报告剩余待确认项。

## 工作流

### 阶段 1 取证（自动）

先读 `references/templates.md` 掌握骨架，读 `references/samples.md` 了解样例的学/不学。

- 判断模式：有 `README.md` → 改进模式；无 → 生成模式。
- 扫描仓库：manifest（package.json / pyproject.toml / Cargo.toml / go.mod 等，含 scripts 与入口）、目录结构与项目类型（库 / CLI / 服务 / 应用）、可运行线索（Makefile、docker-compose、CI）、现有文档（docs/、CONTRIBUTING、LICENSE、CHANGELOG）、已有翻译文件（README-zh.md 等）、git remote 与 log（组织、活跃度、停更线索）。
- 改进模式：逐节诊断已有 README，产出"保留 / 重写 / 删除 / 新增"清单。
- 超小项目（单文件、核心代码 <500 行）：允许裁剪为最小节集合（名称+一句话 / 用法 / 许可），不硬凑章节。
- Monorepo：默认只处理根 README；用户明确指定子包才处理该子包。

### 阶段 2 补缺访谈（只问查不到的）

成组提问，附上你的推断让用户确认，而非从零回答：

1. 目标读者（新用户 / 贡献者 / 集成方）？
2. 项目解决什么问题、与同类差异？
3. 成熟度承诺（alpha / beta / 稳定 / 停更）？
4. 可选节取舍（News / Architecture / Ecosystem / Community / Citation / 语言 switcher / ToC）？

答不上来的记"待确认"，绝不编造。语言：改进模式默认保持原语言；生成模式依据仓库信号提议一种主语言并由用户确认。

### 阶段 3 大纲 gate

输出：章节大纲（核心节 + 选中的可选节）、每节要点、保留/重写清单（改进模式）、素材缺口。
**用户批准前不得动笔。**

### 阶段 4 成稿

按 `references/templates.md` 各节规范写作，遵守篇幅预算（正文 150–400 行；>500 行逐节自问"这内容属于 README 还是 docs"）。

写入规则：直接写 `README.md`；覆盖已有文件且非 git 仓库时，先把原文件备份到系统临时目录（备份路径写进报告）；git 仓库靠 `git diff` 兜底。全程只碰 README.md。

### 阶段 5 自检

按 `references/verification.md` 执行五条回验，产出核对报告（已核实 / 待确认 / 缺失提示 / 备份路径）。存在未核实项时如实说明，不得声称完成。

## 反触发

- 非软件仓库（awesome list、数据集、纯文档站）→ 说明 genre 不同后拒绝，不硬套软件骨架。
- 请求创建/修改 README.md 以外的文件 → 拒绝并说明。

## References

| 文件 | 何时读 |
|------|--------|
| `references/templates.md` | 阶段 1 起：骨架、各节规范、Hero HTML 最小集、badge 白名单、篇幅预算 |
| `references/verification.md` | 阶段 5：五条回验的执行细则与报告格式 |
| `references/samples.md` | 动笔前：4 份样例的结构分析与学/不学清单 |
