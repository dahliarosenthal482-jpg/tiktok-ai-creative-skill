# Agent Protocol

## System Core 启动流程

任何 Work 启动时，必须按以下顺序完成系统级上下文恢复：

1. 识别 System，读取根目录 `SYSTEM_VERSION.md`。
2. 读取 `SYSTEM_CORE/` 中的系统架构、Agent 管理、任务管理和系统规则。
3. 读取 Agent Registry：`MEMORY/AGENT_REGISTRY.md`。
4. 读取 Project Registry：`PROJECTS/_REGISTRY.md`。
5. 读取当前任务及其所属 Project 状态、任务队列和 Session 绑定。
6. 按任务限制和系统规则执行。
7. 按 Task Protocol 与 Output Standard 提交结果并写回相关记录。

## Work 启动流程

任何 Work 开始任务前，必须按以下顺序完成上下文同步：

1. 读取 `GLOBAL_SKILL/AGENT_PROTOCOL.md`。
2. 读取 `MEMORY/DECISION_LOG.md`。
3. 读取对应的 `ACTIVE_PROJECTS/{project}/PROJECT_STATE.md`。
4. 从项目状态与任务队列中确认当前 `TASK`，并核对 Session 绑定信息后再执行。

若项目、任务或 Session 绑定不明确，停止执行并先完成同步，禁止依赖单个 Work 的本地记忆推断。

## 自动恢复与任务占用检查

当 Work 打开项目时，必须先判断：

1. 当前是否存在对应的 `ACTIVE_PROJECTS` 项目目录。
2. 项目目录中是否存在 `TASK_QUEUE.md`。
3. `TASK_QUEUE.md` 中是否存在未完成任务。
4. `MEMORY/AGENT_REGISTRY.md`、Session 绑定信息或任务记录是否显示其他 Agent 已占用该任务。

只有在项目、任务队列和任务归属均确认后才可执行。若任务已被其他 Agent 占用，停止执行并选择其他未占用任务或等待重新分配。

禁止多个 Agent 同时修改同一个任务。Agent 开始任务前必须登记占用状态，完成或释放任务后必须及时更新 Agent Registry、Task Queue 和 Session 信息。

## Product Intelligence 执行规则

所有 Product Intelligence 任务必须遵守 `SYSTEM_CORE/PRODUCT_INTELLIGENCE_STANDARD.md`：

1. 必须先完成 Source Collection，再进入 Fact Extraction。
2. 必须建立 Product Source Map，并为产品事实保留可追踪来源。
3. 必须完成 Visual Asset Extraction 和 Visual Verification。
4. 未完成 Visual Verification，禁止进入 Video Production。
5. 禁止将 AI 推测作为已确认事实写入 Product Profile。

### Product Intelligence Agent 视觉采集顺序

Product Intelligence Agent 必须按以下顺序检查视觉来源：

1. Owner Assets
2. Amazon
3. Kalodata
4. TikTok Shop
5. Supplier

不得因为单一来源失败而结束视觉采集。必须记录失败原因并继续检查下一可用来源；不同来源出现视觉冲突时，禁止自动覆盖，必须等待 Owner Review。

### Product Intelligence Agent 必需输出

Product Intelligence Agent 的完整输出必须包含：

1. Product Facts
2. Visual Intelligence
3. Customer Intelligence
4. Purchase Objection Map

使用 Marketplace 来源前必须完成 Parent Product、Variants、SKU、Selected Variant 和 Visual Match 解析，禁止默认使用页面当前 Variant 作为产品身份。

## Market Intelligence 执行规则

所有 Market Agent 必须遵守 `SYSTEM_CORE/MARKET_INTELLIGENCE_STANDARD.md`。完整输出必须包含：

1. Commerce Intelligence
2. Video Intelligence
3. Customer Intelligence
4. Opportunity Analysis
5. Evidence Summary
6. Risk Items

Market Agent 禁止只输出竞品列表。必须同时提供成交数据、内容数据、消费者信号和证据支持的策略机会；缺失模块必须明确标记为不完整。

## Work 完成流程

任务完成后，必须：

1. 将执行结果写入对应项目的 `EXECUTION_LOG.md`。
2. 更新对应项目的 `PROJECT_STATE.md`，确保状态、当前任务和下一步保持最新。
3. 提供 Commit Hash。
4. 提供 Changed Files。
5. 提供 Evidence Summary。
6. 提供 Risk Items；没有已知风险时明确填写 `None`。

Work 反馈不等于 Final Approval。Work Agent 禁止自行将任务标记为 `APPROVED`。Final Approval 必须由 ChatGPT Strategy Brain 按 `SYSTEM_CORE/SUPERVISOR_REVIEW_STANDARD.md` 和 `GLOBAL_SKILL/REVIEW_CHECKLIST.md` 完成 Supervisor Review 后给出。

Work 完成执行并提交产物后，只能将执行结果状态标记为 `EXECUTED`，不能标记为 `APPROVED`。Supervisor Review 负责输出 Review Decision：`APPROVED`、`NEEDS_REVISION` 或 `REJECTED`。

所有跨 Work 共享上下文以 GitHub 仓库中的文件为准。
