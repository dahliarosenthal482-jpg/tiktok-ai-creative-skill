# System Architecture

## System

AI TikTok Shop Operating System 由五个相互隔离、通过 GitHub 仓库同步的层组成。

## Operating Layers

### Layer 1 — Strategy Brain

ChatGPT 负责战略、任务拆解、优先级和最终决策。

### Layer 2 — Supervisor Review Layer

ChatGPT Strategy Brain 根据 GitHub Commit、Diff、文件、状态和证据独立审核 Work 结果，并控制下一阶段准入。

### Layer 3 — Execution Agents

Work Agents 负责执行、记录、提交产物和风险披露，不拥有最终批准权限。

### Layer 4 — Skills

提供跨项目复用的标准能力。

### Layer 5 — Projects

提供相互隔离的产品工作区、任务状态、证据和输出。

Memory 作为支持五层运行的长期知识平面，保存系统经验、决策与 Agent Registry，不替代任何审核证据。

## Components

### ChatGPT — Strategy Brain

负责战略分析、任务拆解、决策、审核和优先级管理。将可执行任务按统一任务协议分配给 Work Agents。

### Work Agents — Execution Layer

负责执行已分配任务、维护执行记录并提交结果。Work Agents 不依赖单个会话记忆，必须从仓库恢复上下文。

### Skills — Reusable Capabilities

提供可跨项目复用的能力。Skill 知识不得包含单个产品的专属数据。

### Projects — Product-specific Workspaces

通过 `PROJECTS/_REGISTRY.md` 维护项目索引，并在 `ACTIVE_PROJECTS/` 中隔离保存各产品的状态、任务、资料和执行结果。不同 Project 之间不得混用产品上下文。

### Memory — Long-term Knowledge

保存系统级经验、长期决策和 Agent 注册信息。产品实例资料不得写入系统级 Memory 或 Skill Knowledge。

## Relationships

1. ChatGPT 根据系统规则和 Memory 制定决策并创建任务。
2. Task Management 将任务分配给已注册且具备所需 Capability 的 Work Agent。
3. Work Agent 调用适用 Skills，在指定 Project 内执行任务。
4. Work Agent 将结果写回 Project、Session 和执行记录。
5. 经审核可复用的经验进入 Memory；产品专属信息继续留在对应 Project。
6. Work Agent 提交 GitHub 产物后，Supervisor Review Layer 验证结果并由 Strategy Brain 给出 Final Approval。
