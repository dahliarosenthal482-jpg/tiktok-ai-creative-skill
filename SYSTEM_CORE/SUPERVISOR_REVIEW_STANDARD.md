# Supervisor Review Standard v1.0

## Purpose

Supervisor Review Layer 是独立于 Work Execution 的验证与审批层。它由 ChatGPT Strategy Brain 执行，用可追踪证据判断 Work Agent 的结果是否真实、完整、合规，并决定任务能否进入下一阶段。

## Review Responsibilities

Supervisor 必须验证：

1. Task 完成真实性。
2. GitHub 产物一致性。
3. 文件变化范围。
4. 数据来源合规。
5. 状态流转正确。
6. 是否满足进入下一阶段条件。

## Review Flow

```text
Work Execution
↓
Commit GitHub
↓
Supervisor reads Commit, Diff, Files, Project State, Task Queue, Output Reports
↓
Generate Review Result
```

Supervisor 必须以 GitHub 中已提交的产物为审核对象。未提交的本地结果、Work 自述或会话摘要不能单独作为最终批准依据。

## Required Review Inputs

- Task Request 与 Completion Criteria
- Commit Hash
- Commit Diff
- Changed Files
- Project State
- Task Queue
- Output Reports
- Evidence Summary
- Risk Items

若关键输入缺失，Supervisor 不得输出 `APPROVED`。

## Review Status

### APPROVED

证据充分，提交产物与任务要求一致，文件范围合规，状态正确，并满足进入下一阶段条件。

### NEEDS_REVISION

结果可修正，但存在缺失、不一致、证据不足、范围偏差或状态问题。必须列出问题和明确的修订要求。

### REJECTED

结果不可信、违反限制、无法验证、严重越权或不具备可修正的任务基础。必须记录拒绝原因和后续处理建议。

## Validation Rules

### Task Completion Authenticity

将 Work 声明的 Completed Actions 与 Commit、Diff、文件内容和 Completion Criteria 逐项核对。

### GitHub Artifact Consistency

确认报告中的 Commit Hash、Changed Files 和实际 GitHub 提交一致；确认引用文件存在于对应提交中。

### File Scope

确认所有文件变化均在任务授权范围内。发现未授权产品、系统、Session 或 Registry 变更时，必须记录为 Issue。

### Source Compliance

确认数据结论具有可追踪来源，来源等级、验证状态和限制符合相关系统标准；未经确认的数据不得伪装为事实。

### State Transition

确认 Project State、Task Queue、Agent Registry 和 Session 状态之间一致，且不存在跳过审核的阶段推进。

### Next-stage Gate

只有满足当前阶段 Completion Criteria 和所有系统门禁时，Supervisor 才能批准进入下一阶段。

## Review Authority

### ChatGPT Strategy Brain

负责 Final Review、审核决策、下一阶段准入和修订要求。

### Work Agent

负责 Execution、证据整理、产物提交和风险披露。

Work Agent 禁止自行将任务或审核结果标记为 `APPROVED`。Work 反馈不等于 Final Approval；只有 Supervisor Review 可以产生最终审核状态。

## Review Output

审核结果必须使用 `ACTIVE_PROJECTS/_TEMPLATE/REVIEW_REPORT.md` 的结构，并明确记录审核范围、验证结果、Issues、Decision 和 Next Action。
