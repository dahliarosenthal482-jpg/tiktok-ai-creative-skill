# Agent Protocol

## Work 启动流程

任何 Work 开始任务前，必须按以下顺序完成上下文同步：

1. 读取 `GLOBAL_SKILL/AGENT_PROTOCOL.md`。
2. 读取 `MEMORY/DECISION_LOG.md`。
3. 读取对应的 `ACTIVE_PROJECTS/{project}/PROJECT_STATE.md`。
4. 从项目状态与任务队列中确认当前 `TASK`，并核对 Session 绑定信息后再执行。

若项目、任务或 Session 绑定不明确，停止执行并先完成同步，禁止依赖单个 Work 的本地记忆推断。

## Work 完成流程

任务完成后，必须：

1. 将执行结果写入对应项目的 `EXECUTION_LOG.md`。
2. 更新对应项目的 `PROJECT_STATE.md`，确保状态、当前任务和下一步保持最新。

所有跨 Work 共享上下文以 GitHub 仓库中的文件为准。
