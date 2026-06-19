<div align="center">

# GK1200 维修手册查询 Skill

**高金 GK1200（手册内亦称 BX500 / BX1200）摩托车维修手册的查询助手**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Agent Skill](https://img.shields.io/badge/Agent-Skill-d97757.svg)](SKILL.md)

[English](./README.en.md) ·**简体中文**

</div>

用自然语言问扭矩、保养周期、油液规格、拆装步骤，agent 直接检索手册作答；支持识图的 agent 还能解读整页图解——不用再自己翻 PDF 找页码。

## 功能特性

把整本 GK1200 维修手册整理成「可被 agent 直接查询」的 skill。它遵循通用的 skill 规范，**不限于 Claude Code**，任何支持 skill 机制的 agent 都能加载使用。

- **常查硬数据内置「快查表」** — 扭矩、保养周期、油液规格、整车参数、火花塞、胎压、缸压、电气，秒答，无需检索全文。
- **细节按主题索引定位** — 手册全文可被 `grep`，内置主题索引关键词直达相关小节。
- **图解按需给整页图** — 涉及拆装、走线等图解时，提供对应整页图（每页一张、无碎片），支持识图的 agent 可直接解读。
- **安全数据多源并列** — 手册同一部位在不同章节给出的扭矩值若不一致，会把多个来源并列、提示以原书为准。

## 目录结构

```
gk1200-repair/
├─ SKILL.md     # skill 入口：触发描述 + 快查表 + 主题索引 + 看图规则
├─ manual.md    # 手册全文，图链接指向整页图
└─ pages/       # 184 页整页图（WebP）
```

## 安装

把本仓库克隆或复制到 agent 的用户级 skill 目录，使其最终位于 `<skills>/gk1200-repair/`，然后重启 agent（新建会话）加载，直接提问即可触发。

以 Claude Code 为例，skill 目录为：

| 平台 | skill 目录 |
| --- | --- |
| macOS / Linux | `~/.claude/skills/gk1200-repair/` |
| Windows | `%USERPROFILE%\.claude\skills\gk1200-repair\` |

> [!NOTE]
> skill 内引用自身文件均采用「相对 skill 基目录」的写法，克隆到任意路径都可用；其他支持 skill 的 agent 请放到其约定的 skill 目录。

## 用法示例

- GK1200 后轮轴螺母扭矩多少？
- 机油多久换一次、加多少？
- 火花塞什么型号、间隙多少？
- 节气门体怎么拆？

> [!TIP]
> 最后一个问题会返回拆卸步骤 + 对应整页图；支持识图的 agent 会直接解读图中部件、拆装顺序与走线。

## 看图：两类 agent 都兼容

- **不具识图能力的 agent / 你本人** — skill 给出整页图路径和图旁说明文字，自行打开查看。
- **具备识图能力的 agent** — 直接读取整页图并结合问题解读（部件、拆装顺序、走线等）。

> [!WARNING]
> 扭矩值是安全数据。本手册同一部位在不同章节存在**不一致**的扭矩值，skill 会把多个来源值并列并提示以原书为准、取保守做法。实际作业请以纸质 / 官方手册为最终依据。

---

<div align="center">
以 <a href="LICENSE">MIT</a> 许可发布
</div>
