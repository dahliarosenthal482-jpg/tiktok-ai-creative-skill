# Agent Protocol

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

## Work 完成流程

任务完成后，必须：

1. 将执行结果写入对应项目的 `EXECUTION_LOG.md`。
2. 更新对应项目的 `PROJECT_STATE.md`，确保状态、当前任务和下一步保持最新。

所有跨 Work 共享上下文以 GitHub 仓库中的文件为准。
