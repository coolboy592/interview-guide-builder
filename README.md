# interview-guide-builder

为任意项目搭建"面试指导书工作区"并逐章成书的 Agent Skill。沉淀自 akashic-agent 项目的完整实践：可复用的是思考方式与编写标准（两层产物+深度标尺、黄金样例锚定、执行哲学+极简流程），不是任何项目特定事实。方法论与内容均为工具无关，可装入任何支持 SKILL.md 目录格式的编码 agent（ZCode、Claude Code、Codex、OpenCode 等）。

**流程**：定界 → 建工作区（规则入口/事实边界/事实包/执行手册）→ 黄金样例定稿 → 一章一任务写作与验收 → 产出不合意时诊断规格。

**章节产物为双层结构**：口述层（叙述型=五段讲稿可直接口述；深挖型=400～600 字压缩导语，完整讲稿只保留在总述章，追问要点按 30～90 秒可口答密度组织）+ 支撑层（机制详解 / 简历效果↔实现技术对照 / 公平的替代方案对比 / 高概率追问与要点）。

## `shixi` 分支：实习项目适配（2026-09）

`main` 是通用基线；`shixi` 分支在实习项目（大模型后训练 OPSD/SDPO）完整实战并经第三方评审后落盘的适配，可直接用于"实习经历"类项目的面试指导书编写：

- **深挖型模式贯通**：启动 prompt 不再硬编码口述层篇幅，引用工作区规则入口选定模式；skill 摘要与验收条款区分叙述型/深挖型。
- **五段模板弹性化**：五段降为内容完备性参考（顺序与详略按章自主）；未解决的真实问题允许按"现象→判断→尝试→观察→下一步"如实收尾，事实包的踩坑记录分"已闭环/未闭环"两模板，不虚构修复闭环——适配含失败实验的实习项目。
- **真题转换原则**：面经真题经"原题→考察倾向→本项目对应问题"转换后使用；原题仅存档，不按题数分配篇幅，题面内容本项目未涉及的（如其他项目的 SFT/DAPO）不计为覆盖缺口。
- **黄金样例双场景规格**：深挖型项目样例须覆盖一条工程排障回答 + 一条效果判断回答，理解检查迁移到追问层。
- **事实增量交接出口**：章节验收采纳的新事实由定稿指令汇总上报、用户决定写入边界文件或事实包，不新增状态机。
- **公共事实底稿先行**：跨章公共事实（测评口径、算法路径、实验身份）先于打样冻结——章节依赖的是其他章的事实而非成稿。

检出该分支：`git clone -b shixi https://github.com/coolboy592/interview-guide-builder.git`

## 安装

克隆本仓库后，把 `interview-guide-builder/` 整个目录放入你所用的 agent 工具的 skills 根目录（使 `<skills根>/interview-guide-builder/SKILL.md` 存在）：

```bash
git clone https://github.com/coolboy592/interview-guide-builder.git
```

| 工具 | 用户级（所有项目可用） | 项目级（仅当前项目） |
| --- | --- | --- |
| ZCode | `~/.zcode/skills/`（或 `~/.agents/skills/`） | `<项目>/.zcode/skills/`（或 `.agents/skills/`） |
| Claude Code | `~/.claude/skills/` | `<项目>/.claude/skills/` |
| Codex | `~/.codex/skills/` | — |
| OpenCode | `~/.config/opencode/skills/` | `<项目>/.opencode/skills/` |

例（Codex）：

```bash
cp -r interview-guide-builder ~/.codex/skills/interview-guide-builder
```

多数工具在会话启动时索引 skills；安装后如未生效，开一个新会话再试。skill 靠 SKILL.md 的 description 自动触发，无需手动配置。

**兜底用法（任何 agent 工具，含不支持 skill 机制者）**：把本仓库克隆进项目内，在项目的 `AGENTS.md`（或所用工具的全局指令文件）中加一句引用：

```markdown
当用户要求准备项目面试讲解/面试指导书时，按 interview-guide-builder/SKILL.md 定义的流程执行，模板与参考文件在该目录的 templates/ 与 references/ 下。
```

## 结构

```
SKILL.md                          思考方式、三阶段流程、诊断原则
templates/workbench-readme.md     工作区规则入口模板（产物定义/五段模板/硬性标准）
templates/fact-boundaries.md      事实边界模板（术语/数字口径/禁用结论）
templates/fact-packet.md          事实包模板（只放事实，不放写作指令）
templates/execution-playbook.md   执行手册模板（启动 prompt/验收要点/返修模板）
references/golden-sample-reference.md  黄金样例原文参考与新样例起草方法
```

## 使用

在你的 agent 工具中对任意项目表达："面试讲项目 / 帮我写面试指导书 / 把这个项目整理成面试材料"。skill 会先与你定界（面试场景、简历能力条目、事实来源），再搭建工作区、与你逐句定稿黄金样例，然后进入一章一任务的写作与验收循环。各章写作建议一章一个新会话（见执行手册模板），任何支持多会话的 agent 工具均可执行。
