# Agent Management

所有 Work Agent 必须在 `MEMORY/AGENT_REGISTRY.md` 中登记，未登记的 Agent 不得认领任务。

## Agent Identity Fields

Agent ID:

Role:

Capability:

Status:

Current Assignment:

## Management Rules

1. `Agent ID` 必须唯一且稳定。
2. `Role` 描述 Agent 的系统职责。
3. `Capability` 用于判断 Agent 是否具备任务执行条件。
4. `Status` 必须反映 Agent 当前是否可用、执行中、已完成或被阻塞。
5. `Current Assignment` 必须指向当前 Project 和 Task；没有分配时填写 `None`。
6. Agent 认领、释放或完成任务时，必须同步更新 Agent Registry。
