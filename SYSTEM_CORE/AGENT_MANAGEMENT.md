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

## Agent Identity Binding Rule

每个任务必须满足以下身份绑定：

`Task Executor = Session Agent = Commit Author`

Task Executor 是任务队列中登记的执行者；Session Agent 是当前 Session 记录中的 Agent；Commit Author 是实际 Git Commit 作者。三者必须使用同一个 Agent ID。

禁止 Agent A 执行、Agent B 提交。禁止两个 Agent 同时声明同一任务的执行归属。

Supervisor 发现任一身份不一致时，必须记录：

`IDENTITY_MISMATCH`

存在 `IDENTITY_MISMATCH` 的任务必须进入 `NEEDS_REVISION`，在完成 Agent Registry、Session、Task Queue 和提交归属修正前不得批准。
