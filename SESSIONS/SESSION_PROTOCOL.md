# Session Protocol

每个 Work Session 必须使用独立 Session 记录完成以下流程。

## 1. 启动

读取 `GLOBAL_SKILL/WORK_BOOTSTRAP.md`、`SYSTEM_CORE/`、Agent Registry、Project Registry 和当前任务，确认 Agent 身份与系统版本。

## 2. 绑定项目

将 `Assigned Project` 绑定到 Project Registry 中已登记的 Project，并读取该 Project 的状态和任务队列。未登记 Project 不得执行。

## 3. 绑定任务

将 `Assigned Task` 绑定到唯一 Task ID，确认任务已分配给当前 Agent 且未被其他 Agent 占用，并将 Session 状态更新为执行中。

## 4. 提交结果

按照 Task Result 和 Output Standard 写回结果，更新项目状态、任务队列、执行日志、Agent Registry 和 Session 状态，然后提交到 GitHub。
