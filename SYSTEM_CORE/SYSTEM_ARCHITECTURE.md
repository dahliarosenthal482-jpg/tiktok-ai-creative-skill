# System Architecture

## System

AI TikTok Shop Operating System 由五个相互隔离、通过 GitHub 仓库同步的层组成。

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
