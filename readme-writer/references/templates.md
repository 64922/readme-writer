# README 骨架与各节规范

## 骨架总览

核心节（按序，7 个）：Hero → What/Why → Quick Start → Usage/Examples → 深入链接 → Contributing → License。

可选节（证据门控 + 用户确认）：News/Releases、Architecture/How it works、Ecosystem/Partners、Community、Citation、语言 switcher、ToC/锚点导航。

铁律：任何节缺素材 → 省略或降级为一句，禁止空壳、禁止编造。

## 核心节

### 1. Hero（首屏）

组成：项目名（H1）+ 一句话定位（给谁、解决什么）+ 仅真实 badge + 真实首图（如有）。

- 一句话定位 ≤2 行，不堆形容词。
- 图片：只用仓库真实存在的资产（logo、截图、架构图）；alt 必填；首屏 ≤1 张主图 + logo；GIF 提醒仓库体积风险，优先静态图。
- 居中 HTML 最小集模板：

````html
<div align="center">
  <img src="./assets/logo.png" alt="项目名" width="120">
  <h1>项目名</h1>
  <p>一句话定位：给谁、解决什么问题。</p>
  <p>
    <a href="https://example.com"><img src="https://img.shields.io/..." alt="说明"></a>
  </p>
</div>
````

- HTML 只用 GitHub 稳定渲染的最小集：`<div align="center">`、`<img width>`、`<details>/<summary>`、`<br>`、`<hr>`。渐变、复杂内联 style、装饰性花活不用——跨渲染器易碎。
- **Badge 白名单**（只允许四类）：
  1. CI / 构建状态
  2. 包版本 / 下载量
  3. License
  4. 文档 / 社区入口

  人气类（star-history、trendshift 等）不主动加；仓库已有或用户明确要求才加。总数 ≤2 行、≤8 个；每个必须点击指向真实目标；装饰性假 badge 一律禁止。
- Emoji：章节标题做视觉锚点，每节 ≤1 个、全篇风格统一；正文克制。
- 语言 switcher：仅当仓库已有真实翻译文件（README-zh.md 等）才加，只链真实存在的；不创建翻译文件。

### 2. What / Why

- 1 段说明（是什么、给谁、解决什么）+ 要点式特性列表（每条能指到代码或文档）。
- 诚实边界：成熟度（alpha/beta/稳定）、已知限制、不适用场景——只写事实。
- 停更/归档项目：加一行状态说明，不煽情。

### 3. Quick Start（README 最高价值区）

四件套缺一不可：

1. 前置条件（运行时版本、系统依赖、账号/Key）
2. 安装（命令可直接复制执行）
3. 最小可用示例
4. 预期输出（让读者知道自己成功了没）

- 命令必须与仓库事实对得上（manifest scripts / Makefile / docker-compose / CI）。
- 安装路径 ≤3（如 pip / 源码 / Docker）；长参数表、配置项表外链 docs。
- 需要 API Key 的：给出获取入口；示例里用占位符，禁止出现真实密钥。

### 4. Usage / Examples

- 1–2 个真实用例，标题写需求场景（如"用自然语言查询你的文档"），不写"Example 1"。
- 更长内容用 `<details>` 折叠或链接 docs。
- 示例代码必须对应仓库里的真实 API/命令（静态核对）。

### 5. 深入链接

- docs / API 参考 / 论文 / 相关项目；只链真实存在的目标。
- 仓库没有 docs 时写清深入内容的实际位置（代码注释、Wiki），不虚构。

### 6. Contributing

- 有 CONTRIBUTING.md → 链接它；没有 → 一句话（欢迎 issue/PR）或省略。
- 不编造贡献流程细节。

### 7. License

- 有 LICENSE 才写，名称与 LICENSE 文件一致，并链接该文件。
- 没有则省略（收尾报告提示缺失，不代建）。

## 可选节（证据门控 + 用户确认）

| 节 | 加入条件 | 写作要点 |
|----|---------|---------|
| News / Releases | 有真实 release / changelog / 更新记录 | 只留最近 3–5 条；完整历史外链 release 页或 `<details>` 折叠 |
| Architecture / How it works | 有真实架构图或可讲清的机制 | 图用真实资产；机制描述与代码一致 |
| Ecosystem / Partners | 真有合作方 / 衍生项目 | 只链真实的，不暗示不存在的合作关系 |
| Community | 有真实社群入口（Discord / 微信群 / 论坛） | 只列有效的 |
| Citation | 有论文 / DOI | 给 BibTeX；作者与发表信息与论文一致 |
| 语言 switcher | 仓库已有真实翻译文件 | 只链真实存在的；不创建翻译文件 |
| ToC / 锚点导航 | README >300 行或用户要求 | 锚点与真实标题对得上、可跳转 |

## 篇幅预算

- 正文（不含折叠内容）150–400 行；>500 行触发逐节审查："这内容属于 README 还是 docs？"
- 仓库没有 docs/ 且用户保持单文件 → 允许超标，但收尾报告标注"建议迁移到 docs/"。
- 只链接既有 docs；绝不新建 docs 文件。

## 写作风格

- 语气：库/工具类克制精确；产品类可适度热情；禁无实据的空洞形容词（powerful、revolutionary、state-of-the-art）。
- 可扫读：代码块优先于段落；段落 ≤3 行；小标题分层；表格只在参数/对比时用。
- 术语保留英文原词（token、embedding、CLI），正文不中英混排。
- 草稿阶段随手记录每条命令/数字/链接的来源，供阶段 5 回验。
