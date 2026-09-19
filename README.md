# interview-guide-builder

为任意项目搭建"面试指导书工作区"并逐章成书的 Agent Skill。沉淀自 akashic-agent 项目的完整实践：可复用的是思考方式与编写标准（两层产物+深度标尺、黄金样例锚定、执行哲学+极简流程），不是任何项目特定事实。方法论与内容均为工具无关，可装入任何支持 SKILL.md 目录格式的编码 agent（ZCode、Claude Code、Codex、OpenCode 等）。

**流程**：定界 → 建工作区（规则入口/事实边界/事实包/执行手册）→ 黄金样例定稿 → 一章一任务写作与验收 → 产出不合意时诊断规格。

**章节产物为双层结构**：口述层＝可口述导语（约 400～600 字参考，完整讲稿只保留在总述章；追问要点按 30～90 秒可口答密度组织）＋ 按问题需要选取的支撑内容（机制详解 / 观察与数据 / 设计与评价 / 对照 / 追问，不要求齐全）。

## `shixi` 分支：实习项目适配（2026-09，v2 问题驱动版）

`main` 是通用基线；`shixi` 分支在大模型后训练实习项目（OPSD/SDPO）完整实战并经两轮评审迭代，可直接用于"实习经历"类项目的面试指导书编写。**v2（2026-09-19）从章节制改为问题驱动制**：

- **问题驱动成书**：定界产出"项目问题清单"（2～4 个面试官真正会问的问题），写作单元为问题稿；原章节降为"素材域索引"（packet 按素材域分组、多问共用），数据/测评/工程/框架等素材域不因问题重组而丢弃。
- **结构与验收去形式化**：取消每章五项齐全、固定四板块、踩坑修复闭环、每章简历对照与谱系比较、符号/条目计数验收、按"素材最全"定打样；验收集中四问（能否直接回答提问／能否连起约束-机制-观察／能否讲代价与现在的评价／能否区分已做、当时判断与后续建议）。篇幅（导语 400～600 字、总述 2～3 分钟、追问 30～90 秒）仅为参考。
- **事实三层标注**：记录事实／当时判断（记不清保留未知，不补写动机）／现在复盘（有依据的当前评价）；简历约束成果主张，不约束理解深度；材料整理工作不冒充研发经历。
- **打样选最容易偏移的问题**（通常是动机与评价最难讲清的），而非素材最全的章。
- **异议阻塞式**：结构性/规则异议与事实冲突先停下问、裁决后再动笔，不再"先成稿再随稿提"。
- **定界承接记录（03）**：定界变更写承接（新定界、对旧定界与既往评审的保留/撤回、裁决史），不覆盖历史。
- v1 适配（深挖型模式贯通、真题转换原则、事实增量交接出口、公共事实底稿先行）继续有效，并入上述框架。

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
