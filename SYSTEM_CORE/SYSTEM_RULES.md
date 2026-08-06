# System Rules

以下规则属于系统级不可违反规则：

1. Product Data 与 Skill Knowledge 必须分离。
2. 不同 Project 必须隔离，禁止跨项目混用产品资料、任务状态或执行结果。
3. Work 执行必须产生可追踪记录，并写回对应 Project。
4. Work 必须从 GitHub 仓库恢复上下文，不得依赖单个会话记忆作为事实来源。
5. 未注册 Agent 不得认领任务。
6. 多个 Agent 不得同时修改同一个任务。
7. 任务必须经过创建、分配、执行、审核和完成生命周期。
8. 系统级经验只写入 Memory；产品专属信息只写入对应 Project。
9. 所有状态变更和执行结果必须提交到 GitHub 后才视为完成同步。

## Data Boundary Rule

System Knowledge 与 Project Knowledge 必须隔离。

System Knowledge 只能包含跨产品可复用的方法、流程、字段、门禁和验证规则。Project Knowledge 包含具体产品、市场、竞品、价格、采集数据、评论、素材和内容方向，必须保留在对应 Project 中。

Project 经验只能用于验证系统能力是否有效，不能直接成为系统规则。任何拟进入 System Knowledge 的经验都必须先抽象为产品无关规则，并确认不包含真实项目事实、案例、名称、数值、评论或脚本方向。
