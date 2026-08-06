# TikTok Shop Content Commerce Intelligence Framework v1.1

## Purpose

建立适用于所有 TikTok Shop 产品的通用市场情报框架，用于竞品研究、爆款视频分析、市场机会判断和内容策略制定。所有结论必须关联证据、数据周期和置信度，不得只输出竞品列表。

## Module 1 — Commerce Intelligence

### Purpose

判断产品的成交能力、成交结构和销售持续性。

### Required Fields

- Product ID
- Product Name
- Brand
- Marketplace
- Price
- Average Selling Price
- Units Sold / Orders
- GMV
- Video GMV
- Live GMV
- Product Card GMV
- Sales Period
- Data Source
- Confidence

Kalodata 中的出单数量 `Units Sold / Orders` 必须作为核心字段。禁止只看 GMV 判断产品能力；必须结合订单量、价格、销售周期和 Video、Live、Product Card 渠道贡献进行判断。

GMV 或 Orders 缺失时必须明确标记，不得反推或捏造。

## Module 2 — Video Intelligence

### Purpose

分析视频内容表现、流量结构和商品转化能力。

### Video Metadata

- Video ID
- Video URL
- Creator
- Product
- Duration
- Publish Date
- Product Link

### Performance Data

- Views
- Likes
- Comments
- Shares
- Traffic Type
- GMV
- Orders

### Creative Analysis

- Hook Type
- First Frame
- Scene Timeline
- Product Appearance Time
- CTA
- Caption Style
- Audio Pattern

每个视频必须保留来源链接、观察时间和数据周期。内容表现、成交表现和创意特征必须分开记录，禁止仅凭高播放量判断成交能力。

## Module 3 — Customer Intelligence

### Purpose

分析用户购买原因、购买触发因素和阻碍。

### Required Fields

- Customer Motivation
- Purchase Trigger
- Objection
- Negative Feedback
- Positive Feedback
- Customer Language
- Source

允许来源：Reviews、Comments、Q&A。消费者原始表达、模式归纳和策略推论必须分离；所有信号必须记录 Source、样本范围和置信度。

## Module 4 — Opportunity Analysis

### Purpose

综合成交、内容和消费者证据，识别可执行的市场与内容机会。

### Required Outputs

- Competitor Strength
- Competitor Weakness
- Market Gap
- Content Opportunity
- Product Opportunity
- Suggested Strategy

Opportunity Analysis 必须引用前三个模块的证据，不得将无数据支持的假设作为市场机会。

## Module 5 — Competitive Position Intelligence

### Purpose

分析 Premium、Core 和 Entry 价格层级中的竞争位置、价值主张和可执行对策。

### Price Segments

- Premium
- Core
- Entry

### Required Fields

- Price Segment
- Competitor Position
- Value Proposition
- Premium Advantage
- Premium Weakness
- Entry Advantage
- Entry Weakness
- Competitive Opportunity
- Counter Strategy

高价产品不仅是竞争对象，也可能是市场教育来源。分析必须识别 Premium 产品已经建立的用户认知、信任标准和价值语言，并评估其他价格层级如何合法利用该市场教育，而不是简单复制其产品、定价或内容。

Competitive Opportunity 和 Counter Strategy 必须引用 Commerce、Video 或 Customer Intelligence 证据。

## Module 6 — Trend Piggyback Intelligence

### Purpose

分析如何将已有市场趋势迁移到目标产品语境，以获得相关流量和注意力。

### Required Fields

- Trend Pattern
- Original Content Pattern
- Audience
- Emotion Trigger
- Why It Gets Attention
- Adaptation Strategy
- Risk

禁止复制竞品内容、镜头、文案或品牌表达。必须分析趋势背后的注意力机制和迁移条件，形成原创 Adaptation Strategy，并记录品牌错配、受众错配、版权、平台合规和趋势衰退风险。

## Module 7 — Content Conversion Intelligence

### Purpose

分析内容如何从注意力推进到购买行为，并区分播放逻辑与购买逻辑。

### Content Funnel

`Attention → Interest → Desire → Action`

### Required Fields

- Attention Trigger
- Desire Trigger
- Trust Trigger
- Purchase Trigger
- Objection Removal
- CTA Trigger

播放逻辑不等于购买逻辑。高播放、高互动或趋势参与不能自动证明购买转化；必须结合 Orders、GMV、商品链接、CTA、信任证据和异议消除机制判断 Content Conversion。

## Market Intelligence Source Requirements

所有来源必须登记到 `MARKET_SOURCE_MATRIX.md`，并记录 Source ID、Source Type、Source URL、Source Role、Evidence、Information Covered、Confidence 和 Status。

支持的 Source Type 包括：

- Kalodata
- TikTok
- Amazon
- Marketplace
- Review
- Video
- Owner

## Required Outputs

完整 Market Intelligence 输出必须包含：

1. Commerce Intelligence
2. Video Intelligence
3. Customer Intelligence
4. Competitive Position Intelligence
5. Trend Piggyback Intelligence
6. Content Conversion Intelligence
7. Opportunity Analysis
8. Evidence Summary
9. Risk Items

## Quality Gate

Market Intelligence 不得只输出竞品列表。通过质量门槛必须同时包含：

1. 成交数据，包括 Orders 或 Units Sold、GMV、Price、Sales Period 和渠道贡献。
2. 内容数据，包括视频表现与 Creative Breakdown。
3. 消费者信号，包括购买动机、触发因素、正负反馈和异议。
4. 策略机会，包括证据支持的 Market Gap、Content Opportunity 和 Suggested Strategy。
5. 竞争位置，包括 Premium、Core、Entry 的价值差异与 Counter Strategy。
6. 趋势迁移，包括注意力机制、原创 Adaptation Strategy 和风险。
7. 内容转化，包括 Attention、Interest、Desire、Action 的购买链路证据。

任一模块缺失时，输出必须标记为不完整并列入 Risk Items，不得声称 Market Intelligence 已完成。

## Data Boundary

本 Framework 只保存可适用于所有 TikTok Shop 产品的方法、字段、门禁和验证规则。真实项目数据、产品事实、竞品名称、价格、平台采集结果、用户评论和具体脚本方向不得写入本文件。
