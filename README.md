# app-dev-workflow

**从需求讨论到本地测试的六阶段应用开发工作流 skill** · [English summary](#english-summary)

为 AI 编程助手（ZCode / Claude Code / Codex 等 Agent Skills 兼容工具）设计的开发流程约束 skill：把 AI 协作开发从"聊天式随缘"变成"有过关标准的流水线"。

## 它管什么

**六阶段**（每阶段有明确产出与过关标准，未过关不进入下一阶段）：

```
想清楚 → 画出来 → 定架构 → 小步跑 → 测到位 → 稳上线
需求讨论   原型   架构与初始化 迭代开发  本地测试  部署决策
```

**七条总纪律**（约束 AI 的行为）：

1. 双模式门禁：需求与原型人工确认，架构快照确认（不阻塞），之后长跑自治——证据自检、六条安全阀、心跳播报、一次性交付验收
2. 生图前置确认：风格、内容预期、数量三项确认后才生成（成本不可逆 + 审美主观）
3. 能免费验证的别花钱：布局/文案/交互在 HTML 原型里验证
4. 设计系统先行：写界面前必须先过情绪板，禁止直接堆界面
5. 证据反幻觉：过关汇报必须来自实际执行，禁止"应该没问题"式推断
6. 偏离协议：计划外改动必须停下报告获批，禁止顺手就改
7. 文档即接口：下一阶段以上一阶段的 docs/ 文件为唯一事实来源

**三层规则架构**（个人偏好不写死在流程里）：

| 层 | 文件 | 用途 |
|---|---|---|
| skill 默认 | 本仓库内容 | 通用最佳实践 |
| 个人覆盖 | `<skill>/MY-RULES.md`（自建） | 你的长期规则 |
| 项目覆盖 | 项目根 `docs/workflow-rules.md` | 单项目定制 |

## 安装

```bash
# 方式一：通用 skills 安装器
npx skills add x-rush/app-dev-workflow

# 方式二：手动安装到用户级目录
git clone https://github.com/x-rush/app-dev-workflow.git
cp -r app-dev-workflow/skills/app-dev-workflow ~/.agents/skills/
```

安装后**新会话**中说"我要做一个 XX 应用"即自动触发，或以 `/app-dev-workflow` 显式调用。

## 结构

```
skills/app-dev-workflow/
├── SKILL.md                 六阶段主控（触发、过关标准、总纪律、规则分层）
├── references/
│   ├── prototype.md         原型规范（情绪板、生图规范、成本表）
│   ├── dev.md               选型、开发纪律、四层测试法
│   ├── architecture.md      开发前架构设计（最小架构、数据模型、AD 决策记录）
│   └── deploy.md             部署决策（五触发条件、三形态、上线路径）
└── assets/templates/        四个文档模板（需求/数据模型/测试清单/架构决策）
```

## 状态

**v0.2.3 · 早期版本**——流程设计与文档模板完备，但**尚未经大量真实项目实战验证**；欢迎在真实项目中使用并提 issue 反馈。参考实现示例待补（须经使用者验收后收录）。

## 设计出处

流程框架为自研，吸收了成熟框架的文件级设计：[BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD) 的上下文经济学与反幻觉原则；[jeffallan/claude-skills](https://github.com/jeffallan/claude-skills) 的 checkpoint 三选语义、偏离协议与文档即接口。遵循 [Agent Skills 开放标准](https://agentskills.io)。

## License

MIT

---

## English summary

A six-stage app development workflow skill for AI coding agents (requirement discussion → prototype → stack setup → iterative build → local testing → architecture decision). Each stage has explicit deliverables and pass criteria; seven disciplines constrain agent behavior (stage gates, pre-generation confirmation for AI images, evidence-based reporting, deviation protocol, docs-as-interface). Three-layer rule overrides (skill defaults → personal `MY-RULES.md` → per-project `docs/workflow-rules.md`) keep personal preferences out of the core flow. Built to the open Agent Skills standard; works with ZCode, Claude Code, Codex and compatible hosts.
