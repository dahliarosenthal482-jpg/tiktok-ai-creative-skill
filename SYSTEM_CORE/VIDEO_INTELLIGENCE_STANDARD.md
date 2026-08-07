# TikTok Shop Video Intelligence Standard v1.0

## Purpose

建立适用于所有 TikTok Shop 项目的通用 Video Intelligence 数据、拆解、验证和创意输出标准。该标准用于把视频来源、表现、成交、创意结构和可复用模式转换为可审核的 Creative Intelligence，不保存任何真实项目数据。

## 1. Video Dataset Schema

每条视频必须建立独立记录。未知字段必须标记为 `Unavailable` 或 `Need Verification`，不得推测或用聚合数据替代单条视频数据。

### Video Identity

- Video ID
- Platform
- URL
- Creator
- Creator ID
- Account
- Follower Count

### Product Identity

- Product
- Category
- Brand
- Shop
- Product Link

### Performance

- Views
- Likes
- Comments
- Shares
- Save
- Date
- Duration

### Commerce

- GMV
- Orders
- Conversion Signal
- Traffic Type

### Source

- Source URL
- Collection Date
- Confidence
- Verification Status

所有 Metrics 必须记录采集时间和统计口径。商品聚合 GMV、店铺 GMV 或时间窗口总量不得写成单条视频 GMV；无法归因时必须明确标记。

## 2. Video Creative Breakdown Schema

### Hook Analysis — 0–3 Seconds

- Hook Type
- Visual Trigger
- Text Hook
- Audio Hook
- Emotion Trigger

Hook 结论必须引用可观察的首屏、字幕、音频或动作证据。推断的心理机制必须与观察事实分开。

### Scene Structure

每个 Scene 独立记录：

- Scene Number
- Duration
- Scene Purpose
- Location
- Character
- Product Appearance
- Action

Scene 时间必须可回溯到视频时间轴。缺少可播放视频时不得伪造 Scene Structure。

### Product Integration

- First Product Appearance Time
- Product Demo
- Usage Method
- Feature Demonstration
- Proof Element

产品展示内容不得自动成为 Product Fact。功能、用法和 Proof Element 必须与批准的 Product Truth 分开验证。

### Conversion Structure

- Pain Point
- Desire Trigger
- Trust Element
- Objection Handling
- CTA

Conversion Structure 描述内容中的购买推动机制，不代表已证明因果关系。需要 Commerce 数据或测试结果才能提高转化置信度。

## 3. Viral Factor Analysis

每条视频或模式必须分别分析：

- Attention
- Retention
- Engagement
- Conversion

`播放量 ≠ 销售能力`。

必须区分：

### High View Content

以 Views、Retention 或 Engagement 表现突出，但缺少 Orders、GMV、商品点击或其他成交证据的内容。

### High Conversion Content

具有可验证的 Orders、GMV、Conversion Signal、商品点击或其他成交证据，并能与具体视频建立合理归因的内容。

高播放不得自动标记为高转化；高 GMV 也不得在缺少归因时自动归因给某个 Hook、Scene 或 CTA。

## 4. Trend Adaptation Framework

### Required Fields

- Trend Pattern
- Audience
- Emotion
- Why It Works
- Adaptation Opportunity

趋势分析必须识别底层注意力、情绪和参与机制，并形成原创迁移方案。禁止复制竞品或来源内容的镜头、文案和品牌表达。

Adaptation Opportunity 必须记录适用条件、平台风险、品牌错配、受众错配、版权风险和趋势衰退风险。趋势热度不得替代产品适配与合规验证。

## 5. Creative Intelligence Output

Video Intelligence 完成后必须输出：

- Winning Hook
- Scene Pattern
- Character Pattern
- Product Demo Pattern
- CTA Pattern
- Testing Direction

这些输出可供后续 Script Generation 和 AI Video Generation 使用，但在进入生产前必须通过 Product Truth、Visual Lock、Claim Boundary、来源权限和 Supervisor Gate。

`Winning` 只表示在已定义证据窗口和指标下表现较强，不代表跨产品、跨市场或未来表现的保证。

## 6. Evidence Classification

所有结论必须分为：

1. Observed Evidence：视频、指标或来源中直接观察到的信息。
2. Inference：基于证据形成的解释，不得伪装为事实或因果证明。
3. Future Test Direction：待验证的 Hook、Scene、Character、Demo、CTA 或组合假设。

## 7. Required Outputs

完整 Video Intelligence 任务必须产生：

1. Video Dataset
2. Video Source Matrix
3. Video Creative Breakdown
4. Viral Factor Analysis
5. Trend Adaptation Analysis
6. Creative Intelligence Output
7. Evidence Summary
8. Risk Items

## 8. Quality Gate

只有满足以下条件，Video Intelligence 才能标记为完整：

1. 每条视频具有唯一 Video ID、URL 或明确的不可用状态。
2. 来源、采集日期、置信度和验证状态可追踪。
3. Performance 与 Commerce 字段分离，缺失值未被推测。
4. Hook、Scene、Product Integration 和 Conversion Structure 有视频证据支持。
5. High View Content 与 High Conversion Content 明确区分。
6. Observed Evidence、Inference 和 Future Test Direction 明确分离。
7. Creative Intelligence Output 保留适用条件与风险。

缺失任何门槛时必须标记为 `INCOMPLETE`，并写入 Risk Items，不得宣称已经识别稳定爆款或销售因果关系。

## 9. Data Boundary

本标准只保存跨产品可复用的字段、方法、门禁和验证规则。禁止写入产品名称、竞品名称、价格、GMV、真实视频案例、TikTok 账号或任何平台采集数据。真实记录只能保存在对应 Project 中。
