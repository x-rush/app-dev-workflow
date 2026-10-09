# app-dev-workflow

从需求讨论到本地测试的六阶段应用开发工作流，以 [Agent Skills 开放标准](https://agentskills.io) 的 skill 形式实现（SKILL.md + references + templates）。

## 这是什么

一个约束 AI 协作开发纪律的流程 skill：**想清楚 → 画出来 → 定架构 → 小步跑 → 测到位 → 稳上线**。每阶段有明确产出与过关标准，未过关不进入下一阶段；内含原型规范（情绪板先行、生图前置确认）与 AI 协作纪律（一次一个任务、每步 commit、自测后交付）。

## 结构

```
app-dev-workflow/
├── SKILL.md                 六阶段主控（触发、过关标准、总纪律、规则分层）
├── MY-RULES.md              个人覆盖层（本机规则；发布时不随 skill 分发）
├── references/
│   ├── prototype.md         原型规范（情绪板、AI 味自检、生图、成本）
│   ├── architecture.md      阶段2 · 架构与初始化（选型、最小架构、AD 决策）
│   ├── dev.md               阶段3/4 · 开发纪律、任务→可验证目标、四层测试
│   └── deploy.md            阶段5 · 部署决策（五触发、三形态、上线路径）
└── assets/templates/        四个文档模板（需求/数据模型/测试清单/架构决策）
```

## 规则分层

skill 正文是**全流程通用最佳实践**（无个人事件引用，任何项目可用）。两层可覆盖：

- `MY-RULES.md`（skill 目录）：本机个人规则，触发时必读；
- 项目根 `docs/workflow-rules.md`：单个项目的特有需求，优先级最高。

这样个人偏好不写死在流程里——换项目、换需求，只需换覆盖文件，skill 本体不动。

## 安装

```bash
# 方式一：直接克隆/复制到用户级 skill 目录（跨工具通用）
git clone <repo> ~/.agents/skills/app-dev-workflow

# 方式二：通用 skills 安装器
npx skills add <owner>/<repo>
```

安装后新会话中说"我要做一个 XX 应用"即可自动触发，或以 `/app-dev-workflow` 显式调用。

## 修改指南

- 调流程/纪律：改 `SKILL.md`（主控）与 `references/`（细则），纯 markdown；
- 调文档产出：改 `assets/templates/` 下的模板；
- 版本记录：frontmatter `metadata.version`，改动请同步更新。

## 路线图

- [ ] 首次实战验证（真实项目走通六阶段后修订）
- [ ] 参考实现示例（需经使用者验收后放入 `assets/demo-examples/`）
- [ ] 轻量复盘环节（项目收尾时 10 分钟：本周期哪里卡壳/哪个阶段返工最多，写进 docs/ 反哺流程）
- [ ] 英文 README

## 设计出处

流程框架为自研，吸收了成熟框架的文件级设计：BMAD-METHOD 的上下文经济学（"何时不加载"作为设计目标）与反幻觉原则（答案来自运行时而非记忆）；jeffallan/claude-skills 的 checkpoint 三选语义（通过/修改/打回）、偏离协议（计划外改动必须停下获批）与文档即接口（上游产出是下游唯一事实来源）。
