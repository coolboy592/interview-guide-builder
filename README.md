# interview-guide-builder

为任意项目搭建"面试指导书工作区"并逐章成书的 ZCode skill。沉淀自 akashic-agent 项目的完整实践：可复用的是思考方式与编写标准（两层产物+深度标尺、黄金样例锚定、执行哲学+极简流程），不是任何项目特定事实。

**流程**：定界 → 建工作区（规则入口/事实边界/事实包/执行手册）→ 黄金样例定稿 → 一章一任务写作与验收 → 产出不合意时诊断规格。

**章节产物为双层结构**：口述层（五段模板，可直接口述）+ 支撑层（机制详解 / 简历效果↔实现技术对照 / 公平的替代方案对比 / 高概率追问与要点）。

## 安装

```bash
git clone https://github.com/coolboy592/interview-guide-builder.git
cp -r interview-guide-builder ~/.zcode/skills/interview-guide-builder
```

（`~/.agents/skills/` 同为用户级发现根，二选一即可。）安装后**新建会话**生效——skill 目录在会话启动时索引，会话内不热更新。输入 `/` 在 Skills 分组确认，或直接说"我想准备 XX 项目的面试讲解"触发。

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

在任意项目中对 ZCode 表达："面试讲项目 / 帮我写面试指导书 / 把这个项目整理成面试材料"。skill 会先与你定界（面试场景、简历能力条目、事实来源），再搭建工作区、与你逐句定稿黄金样例，然后进入一章一任务的写作与验收循环。
