# 思为小红书知识卡片 Skill

这是一个面向 Codex 的中文 Skill，用于把 AI 基础知识、产品经理学习内容、实践复盘与避坑经验，整理成“思为的新世界”风格的小红书知识卡片。

## 能力

- 用 10 个需求问题锁定受众、目标、论点、素材和转化动作。
- 按知识单元动态规划页数，不为凑页重复内容。
- 自动路由两套品牌主题：知识输入使用科技蓝，经验输出使用成长绿。
- 先交付规划与单张样图，确认后再生成整套图片。
- 统一检查画布、字号、文字、页码、品牌署名与套图一致性。

## 目录

```text
.
├── README.md
├── LICENSE
├── NOTICE.md
└── skill/
    ├── SKILL.md
    ├── agents/openai.yaml
    ├── assets/style-reference.png
    └── references/
        ├── brand-system.md
        ├── production-workflow.md
        └── quality-gate.md
```

## 安装

将 `skill/` 复制到 Codex 技能目录，并将目录名改为 `siwei-xhs-knowledge-cards`：

```bash
cp -R skill ~/.codex/skills/siwei-xhs-knowledge-cards
```

重启 Codex 或开启新任务后，可以显式调用：

```text
Use $siwei-xhs-knowledge-cards 把这份 AI 产品学习笔记做成小红书知识卡片。
```

## 使用前提

图片生成需要当前 Codex 环境可用的图像生成或本地 HTML/SVG 渲染能力。Skill 不内置第三方字体、平台 API 密钥或发布自动化工具。

## 来源与许可

本项目基于 [ziguishian/xhs-visual-director-skill](https://github.com/ziguishian/xhs-visual-director-skill) 修改，在保留其视觉导演工作流思路的基础上，按“思为的新世界”的内容定位、品牌视觉和交付流程进行了精简与重写。本公开版不分发上游的示例、模板或封面资产。详见 [NOTICE.md](NOTICE.md)。

本仓库公开版内容按 [MIT License](LICENSE) 发布。上游版权与许可声明已保留在 [NOTICE.md](NOTICE.md) 中。
