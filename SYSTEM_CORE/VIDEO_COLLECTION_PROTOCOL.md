# TikTok Shop Video Intelligence Collection Protocol v1.0

## Purpose

定义所有 Video Intelligence 数据采集任务的统一选样、排除、验证、质量评级、证据分类和交付规则。本协议只描述通用系统方法，不包含产品、竞品、账号、链接或平台采集数据。

所有采集任务必须同时遵守 `SYSTEM_CORE/VIDEO_INTELLIGENCE_STANDARD.md`、项目授权范围、来源使用权限和平台规则。

## 1. Collection Task Setup

采集开始前必须建立 `VIDEO_COLLECTION_TASK.md`，明确：

- Task ID
- Category
- Market
- Collection Goal
- Selection Rules
- Required Fields
- Quality Target

Task 必须定义采集窗口、目标样本量、允许来源、去重规则、证据用途和停止条件。不得在任务授权外扩大品类、市场或数据范围。

## 2. Video Selection Rules

每条候选视频只能根据可验证证据进入下列最高适用等级；等级不得由主观印象决定。

### Tier A — 商业验证视频

#### Conditions

必须存在：

- GMV
- Orders
- 商品关联
- 明确销售结果

Commerce 数据必须能够合理归因到对应视频，并记录统计窗口、来源和验证状态。聚合商品或店铺数据不得冒充单视频结果。

#### Use

学习高转化结构，包括 Conversion Evidence、Product Demonstration、Trust、Objection Handling 和 CTA。

### Tier B — 流量验证视频

#### Conditions

必须存在：

- 高播放或可比较的播放表现
- 高互动或可比较的互动表现
- 明确商品关联

“高”必须相对于已声明的数据窗口、样本或基准定义，不得无基准使用。

#### Use

学习 Attention、Retention、Engagement、Hook 和 Scene Structure。Tier B 不得自动视为高转化内容。

### Tier C — 趋势参考视频

#### Conditions

- 内容结构明显
- 趋势模式明显
- 商业数据不足或不可验证

#### Use

仅学习趋势机制、受众情绪和原创迁移机会。Tier C 不得作为核心商业训练数据或转化证明。

## 3. Video Exclusion Rules

以下视频禁止作为核心训练数据：

1. 无商品关联视频。
2. 无法确认来源视频。
3. 纯娱乐内容。
4. 重复搬运内容。
5. 无法确认发布时间或作者的视频。
6. 与目标品类无关的视频。

排除视频可以保留最小审计记录，包括 Exclusion Reason、Source、Review Date 和 Reviewer，但不得进入 Winning Pattern、High Conversion 或核心训练样本统计。

若无法确认是否搬运、作者身份或商品关联，必须标记为 `Need Verification`，不得默认纳入。

## 4. Video Data Quality Rating

质量评级与 Selection Tier 分开。Tier 描述用途和证据类型；Quality Grade 描述记录完整性。

### A 级 — Analysis Ready

完整具备：

- URL
- Creator
- Metrics
- Product Link
- Date
- Analysis Ready

同时必须具有 Source、Collection Date、Confidence 和 Verification Status。

### B 级 — Trend Analysis Ready

部分字段缺失，但来源可确认，视频可观察，并足以支持 Hook、Scene、Retention 或 Trend Analysis。所有缺失字段必须列入 Missing Fields。

不得用 B 级样本证明完整 Commerce 转化结构，除非对应 Commerce 字段另有可验证证据。

### C 级 — Visual Reference Only

仅有视觉或结构参考，关键身份、来源、时间、作者、商品关联或指标不完整。

C 级不可作为核心学习数据，不得进入 High Conversion 结论，只能作为低置信度视觉参考。

## 5. Evidence Classification

每条视频的记录和分析必须分别标记：

### Observed Evidence

实际看到或从可验证来源读取的视频内容、身份、指标、商品关联和时间信息。

### Inference

基于 Observed Evidence 形成的受众心理、创意机制或转化解释。

### Future Test

需要通过后续内容测试、A/B Test 或新数据验证的方向。

禁止把 Inference 或 Future Test 写成事实。因果语言必须有明确实验或归因证据支持。

## 6. Video Analysis Priority

采集完成后的分析优先级为：

1. Conversion Evidence
2. Hook Pattern
3. Retention Structure
4. Product Demonstration
5. CTA

播放量不是唯一评价指标。Views、Engagement、Retention、Orders、GMV、商品关联和归因质量必须分开判断。

若 Conversion Evidence 缺失，必须继续分析 Attention 和 Retention，但不得输出 High Conversion 结论。

## 7. AI Generation Connection

合格的采集与分析输出必须支持：

- Winning Hook
- Scene Pattern
- Character Pattern
- Product Demo Pattern
- Emotion Trigger
- CTA Pattern
- Testing Direction

这些字段可供 Script Generation 和 AI Video Production 使用，但必须保留 Selection Tier、Quality Grade、Evidence Classification、Confidence、适用条件和 Risk Items。

任何输出进入生成阶段前必须通过 Product Truth、Visual Lock、Claim Boundary、素材权限和 Supervisor Gate。禁止复制来源视频的镜头、文案或品牌表达。

## 8. Required Collection Outputs

每个 Video Collection 任务必须产生：

1. Video Collection Task
2. Video Dataset
3. Video Source Matrix
4. Video Data Quality Report
5. Exclusion Log
6. Evidence Summary
7. Risk Items

## 9. Completion Gate

任务只有在以下条件满足时才能标记为 `EXECUTED`：

1. 所有入选视频具有 Selection Tier。
2. 所有记录具有 Quality Grade。
3. 所有缺失字段明确列出。
4. 来源与商品关联状态可验证或明确标记未知。
5. 重复内容已识别并排除。
6. Observed Evidence、Inference 和 Future Test 分离。
7. Usage Permission 已记录。
8. Evidence Summary 和 Risk Items 完整。

`EXECUTED` 不等于 `APPROVED`。只有 Supervisor Review 可以决定是否允许数据进入 Video Intelligence 分析或后续生成阶段。

## 10. Data Boundary

本协议只保存跨项目可复用的规则、字段、等级和门禁。禁止写入产品名称、竞品名称、价格、GMV 案例、真实视频链接、账号信息或平台采集数据。真实采集结果只能写入对应 Project。
