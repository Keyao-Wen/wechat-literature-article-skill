# WeChat Literature Article Skill

[![Release](https://img.shields.io/github/v/release/Keyao-Wen/wechat-literature-article-skill?label=release)](https://github.com/Keyao-Wen/wechat-literature-article-skill/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Codex Skill](https://img.shields.io/badge/Codex-skill-2F7D4A)](SKILL.md)

把英文学术论文整理成**中文科研公众号文献推文**的 Codex skill。

`wechat-literature-article` 面向中文科研写作场景，目标不是生成一篇“看起来很流畅”的论文总结，而是把论文信息、摘要、数据与方法、关键结果、数字审计、术语统一、图文对应和 Word/公众号排版串成一个可复用、可审计的写作流程。

> English: A Codex skill for turning academic papers into rigorous Chinese WeChat public-account literature articles.

## 为什么做这个

写科研公众号文献推文，真正麻烦的往往不是翻译摘要，而是这些细节：

- 论文标题、期刊、发表时间、DOI 不能错；
- 方法不能写成一句“用了模型/遥感/统计分析”；
- 关键数字不能漏单位、分母、样本量或不确定性；
- 图不能只是贴上去，要解释它支持了什么结论；
- 术语前后要一致，不能一会儿一个译法；
- 最终文章要干净，能复制进公众号后台或整理成 Word。

这个 skill 的核心思路是：**科研公众号文章应该好读，但也应该可审计。**

它会要求 Codex 保留从论文到推文的证据链：

```text
论文信息 -> 来源梳理 -> 术语表 -> 数字审计 -> 图文对应 -> 中文推文 -> Word/公众号 QA
```

## 适合谁

| 适合 | 不适合 |
| --- | --- |
| 课题组公众号文献介绍 | 一键生成夸张科普爆文 |
| 研究生整理英文论文 | 没有来源材料却要求编完整文章 |
| Nature/Science 风格研究论文解读 | 替代领域专家最终把关 |
| 方法较复杂、图表较多的论文 | 需要制作 PPT 或 slide deck 的任务 |
| 已有中文草稿的学术化精修 | 自动复用没有授权的论文图片 |

## 它能帮你做什么

- 从论文 PDF 草拟中文科研公众号文献推文；
- 把已有草稿改得更学术、更准确、更适合发布；
- 解释数据来源、方法流程、模型逻辑、验证和不确定性；
- 统一术语，减少中英文混用和前后译名不一致；
- 内部审计关键数字，保留单位、分母、样本量和来源；
- 选择核心图，并为每张图写清楚它支持什么结论；
- 检查图文对应，避免“图只是装饰”；
- 清理中文排版，输出适合 Word/公众号后台的文章。

本 skill **不负责制作演示文稿或 slide deck**。如果需要做汇报幻灯片，请使用专门的 presentation 工作流。

## 快速安装

把仓库 clone 到 Codex skills 目录，并把文件夹命名为 skill 需要的名字：

```text
git clone https://github.com/Keyao-Wen/wechat-literature-article-skill.git ~/.codex/skills/wechat-literature-article
```

Windows PowerShell：

```text
git clone https://github.com/Keyao-Wen/wechat-literature-article-skill.git "$env:USERPROFILE\.codex\skills\wechat-literature-article"
```

安装后重启 Codex，或开启一个新对话。

## 复制给 Codex / AI 安装

如果你不想自己敲命令，可以直接把下面这段复制给 Codex 或其他能操作本机终端的 AI：

```text
请帮我安装这个 Codex skill：

仓库地址：https://github.com/Keyao-Wen/wechat-literature-article-skill
目标目录：~/.codex/skills/wechat-literature-article

请执行以下步骤：
1. 如果目标目录已存在，先检查是否是同一个 git 仓库；如果是，就 git pull 更新；如果不是，请先询问我是否覆盖。
2. 如果目标目录不存在，请运行：
   git clone https://github.com/Keyao-Wen/wechat-literature-article-skill.git ~/.codex/skills/wechat-literature-article
3. 安装完成后，提醒我重启 Codex 或开启新对话。
4. 最后告诉我可以这样调用：
   Use $wechat-literature-article to write a Chinese WeChat public-account article from this paper PDF.
```

Windows 用户也可以复制这一版：

```text
请帮我在 Windows 上安装这个 Codex skill：

仓库地址：https://github.com/Keyao-Wen/wechat-literature-article-skill
目标目录：$env:USERPROFILE\.codex\skills\wechat-literature-article

请执行以下步骤：
1. 如果目标目录已存在，先检查是否是同一个 git 仓库；如果是，就 git pull 更新；如果不是，请先询问我是否覆盖。
2. 如果目标目录不存在，请运行：
   git clone https://github.com/Keyao-Wen/wechat-literature-article-skill.git "$env:USERPROFILE\.codex\skills\wechat-literature-article"
3. 安装完成后，提醒我重启 Codex 或开启新对话。
4. 最后告诉我可以这样调用：
   Use $wechat-literature-article to write a Chinese WeChat public-account article from this paper PDF.
```

## 使用示例

从论文 PDF 草拟公众号推文：

```text
Use $wechat-literature-article to write a Chinese WeChat public-account article from this paper PDF.

Please include a rigorous but eye-catching title, paper metadata, a concise abstract translation, detailed methods, main results, explained figures, discussion, and conclusion. Output as Word with clean Chinese typography.
```

精修已有草稿：

```text
Use $wechat-literature-article to revise this draft for WeChat publication.

Make the language more academic, reduce unnecessary English terms, improve the methods and conclusion sections, explain each selected figure, standardize Word fonts, clean Chinese typography, and audit key numbers internally.
```

只有提取文本或信息不完整时：

```text
Use $wechat-literature-article to draft a limited Chinese WeChat literature article from the extracted text below.

Do not invent missing metadata, figures, sample sizes, uncertainty ranges, or DOI information. Clearly mark unavailable facts and list what source materials are still needed for a publication-ready version.
```

更多 prompt 模板见 [examples/prompts.md](examples/prompts.md)。

## 输出质量标准

一个合格输出不应该只是“中文流畅”。它还应该做到：

- 论文标题、期刊、DOI、发表时间等信息准确；
- 方法部分讲清楚数据、样本、模型、计算逻辑、验证和不确定性；
- 关键数字保留单位、分母、样本量、置信区间或不确定性；
- 主要结论能映射到论文正文、图、表或补充材料；
- 术语前后一致，英文缩写首次出现时解释清楚；
- 图像裁剪后坐标轴、图例、色标、panel 标签可见；
- 每张图都有中文解释，并和正文结果对应；
- 最终 Word/文章只包含可发布内容，不混入内部审计表和过程笔记。

更详细的评分表见 [docs/quality-rubric.md](docs/quality-rubric.md)。

## 仓库内容

- `SKILL.md`：Codex skill 的核心工作流和质量要求。
- `examples/prompts.md`：论文转推文、草稿精修、信息不完整场景的 prompt 模板。
- `examples/synthetic-demo/README.md`：无版权风险的虚构示例，展示证据链如何组织。
- `agents/openai.yaml`：Codex 应用侧元数据和默认调用提示。
- `docs/demo.md`：输入、工作流、输出结构的简要说明。
- `docs/quality-rubric.md`：判断文章是否达到发布质量的评分表。
- `ROADMAP.md`：后续改进计划。
- `CHANGELOG.md`：版本更新记录。

## 范围和版权提醒

这个仓库只包含 workflow instructions，不包含论文 PDF、版权图片、文章草稿或生成的 Word 文件。

使用论文图片、图表或原文内容时，请确认你有权在对应公众号、课题组或公开平台中使用。

## 贡献

欢迎贡献：

- 面向不同学科的 prompt；
- 基于 open-access 论文的真实案例；
- 更强的图表、数字、Word 排版 QA checklist；
- 常见失败案例和修正示例；
- 生态、气候、医学、AI 等领域的术语示例。

提交 issue 或 PR 前，请先看 [CONTRIBUTING.md](CONTRIBUTING.md)。

## License

MIT License. See [LICENSE](LICENSE).
