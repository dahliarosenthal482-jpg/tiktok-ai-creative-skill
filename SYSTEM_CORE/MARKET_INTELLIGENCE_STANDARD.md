# Market Intelligence Framework v1.0

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
4. Opportunity Analysis
5. Evidence Summary
6. Risk Items

## Quality Gate

Market Intelligence 不得只输出竞品列表。通过质量门槛必须同时包含：

1. 成交数据，包括 Orders 或 Units Sold、GMV、Price、Sales Period 和渠道贡献。
2. 内容数据，包括视频表现与 Creative Breakdown。
3. 消费者信号，包括购买动机、触发因素、正负反馈和异议。
4. 策略机会，包括证据支持的 Market Gap、Content Opportunity 和 Suggested Strategy。

任一模块缺失时，输出必须标记为不完整并列入 Risk Items，不得声称 Market Intelligence 已完成。
