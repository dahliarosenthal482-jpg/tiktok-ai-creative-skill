# Task Management

所有任务必须使用 `GLOBAL_SKILL/TASK_PROTOCOL.md` 的统一格式，并依次经过以下生命周期。

## 1. Task 创建

定义唯一 Task ID、所属 Project、目标、输入、预期输出、限制和完成标准。

## 2. 分配

根据 Agent Registry 中的 Role、Capability、Status 和 Current Assignment 选择执行者。分配前确认任务未被其他 Agent 占用。

## 3. 执行

执行者绑定 Session 和 Task，按项目范围执行，并持续维护任务状态与执行记录。

## 4. 审核

根据 Completion Criteria 检查结果、输出文件、问题和限制遵守情况。不符合标准的任务返回执行阶段。

## 5. 完成

写入 Task Result 和项目执行记录，更新项目状态、任务队列、Agent Registry 与 Session 状态，并提交到 GitHub。
