# 思为小红书知识卡片 Skill

这是一个可移植的中文 Agent Skill，用于把 AI 基础知识、产品经理学习内容、实践复盘与避坑经验，整理成“思为的新世界”风格的小红书知识卡片。

核心目录遵循 [Agent Skills 开放标准](https://agentskills.io/home)。兼容该标准的 Agent 可以直接安装；支持项目规则、知识文件或自定义指令的其他 Agent，也可以读取同一套 `SKILL.md`、参考资料和视觉资产执行工作流。

## 能力

- 用 10 个需求问题锁定受众、目标、论点、素材和转化动作。
- 按知识单元动态规划页数，不为凑页重复内容。
- 自动路由两套品牌主题。知识输入使用科技蓝，经验输出使用成长绿。
- 先交付规划与单张样图，确认后再生成整套图片。
- 统一检查画布、字号、文字、页码、品牌署名与套图一致性。

## 效果示例

### 科技蓝｜RAG 知识科普

| 封面 | 内页 |
| --- | --- |
| ![科技蓝封面](examples/blue-cover.png) | ![科技蓝内页](examples/blue-inner.png) |

### 成长绿｜Vibe Coding 实践复盘

| 封面 | 内页 |
| --- | --- |
| ![成长绿封面](examples/green-cover.png) | ![成长绿内页](examples/green-inner.png) |

## 兼容方式

| Agent 产品 | 使用方式 | 兼容级别 |
| --- | --- | --- |
| [Codex](https://developers.openai.com/api/docs/guides/tools-skills) | 安装 `skill/` 目录，由 Agent 按描述自动触发或显式调用 | 原生 Skill |
| ChatGPT Skills | 在支持 Skills 的工作区上传技能包，具体入口取决于账号和工作区设置 | 原生导入 |
| [Claude Code](https://code.claude.com/docs/en/skills) | 将 `skill/` 复制到 `~/.claude/skills/siwei-xhs-knowledge-cards` | 原生 Skill |
| [WorkBuddy](https://www.workbuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market) | 下载 [Skill ZIP](dist/siwei-xhs-knowledge-cards.zip)，在 Skills 页面导入本地技能包 | 原生导入 |
| [TRAE](https://docs.trae.cn/ide_rules) | 将仓库放入项目，通过 `.trae/rules/`、`AGENTS.md` 或 `CLAUDE.md` 指示 Agent 读取 `skill/SKILL.md` | 规则适配 |
| 其他 Agent | 将 `skill/SKILL.md` 与其引用的 `references/`、`assets/` 一并加入项目知识或会话上下文 | 手动适配 |

当前版本在 Codex 中完成开发与全流程验证，因此 Codex 是首选运行环境，自动触发、分阶段确认、本地渲染与文件审查的完成度最高。其他 Agent 可按上表使用，但受工具、上下文和渲染能力差异影响，版式一致性与成图质量可能略低，建议先确认一张样图，再批量生成整套图片。

不同产品的自动发现目录、触发语法和工具权限并不相同。没有开放本地 Skill 导入的对话产品，例如部分豆包版本，可以上传这些 Markdown 文件作为项目知识或自定义指令，但不能保证获得本地文件渲染、批量导图和自动调用能力。

## 安装

### Codex

```bash
cp -R skill ~/.codex/skills/siwei-xhs-knowledge-cards
```

重启 Codex 或开启新任务后调用：

```text
Use $siwei-xhs-knowledge-cards 把这份 AI 产品学习笔记做成小红书知识卡片。
```

### Claude Code

```bash
cp -R skill ~/.claude/skills/siwei-xhs-knowledge-cards
```

随后在 Claude Code 中输入 `/siwei-xhs-knowledge-cards`，或直接描述需要生成小红书知识卡片的任务。

### WorkBuddy

下载 [siwei-xhs-knowledge-cards.zip](dist/siwei-xhs-knowledge-cards.zip)，在 Skills 页面选择添加技能并上传。压缩包根目录已经包含 `SKILL.md`。

### 规则型或通用 Agent

把仓库加入 Agent 可读取的项目目录，并使用以下指令：

```text
读取 skill/SKILL.md，并按其中引用的 references 和 assets 完成这套小红书知识卡片。先给出规划和一张样图，确认后再生成整套图片。
```

## 使用前提

目标 Agent 需要具备图像生成能力，或能够运行 HTML/SVG 等本地渲染工具。Skill 不内置第三方字体、平台 API 密钥或发布自动化工具。若 Agent 只能处理文本，它仍可完成选题、页面蓝图、逐页文案、生成提示词和质量审查，但不能直接交付 PNG。

## 目录

```text
.
├── README.md
├── LICENSE
├── NOTICE.md
├── dist/
│   └── siwei-xhs-knowledge-cards.zip
├── examples/
│   ├── blue-cover.png
│   ├── blue-inner.png
│   ├── green-cover.png
│   └── green-inner.png
└── skill/
    ├── SKILL.md
    ├── agents/openai.yaml
    ├── assets/style-reference.svg
    └── references/
        ├── brand-system.md
        ├── production-workflow.md
        └── quality-gate.md
```

`skill/agents/openai.yaml` 只提供 OpenAI 产品的界面元数据。其他 Agent 可以忽略该文件，不影响标准 `SKILL.md` 工作流。

## 来源与许可

本项目基于 [ziguishian/xhs-visual-director-skill](https://github.com/ziguishian/xhs-visual-director-skill) 修改，在保留其视觉导演工作流思路的基础上，按“思为的新世界”的内容定位、品牌视觉和交付流程进行了精简与重写。本公开版不分发上游的示例、模板或封面资产。详见 [NOTICE.md](NOTICE.md)。

本仓库公开版内容按 [MIT License](LICENSE) 发布。上游版权与许可声明已保留在 [NOTICE.md](NOTICE.md) 中。
