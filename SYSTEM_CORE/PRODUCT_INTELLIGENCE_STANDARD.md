# Product Intelligence Standard v1.3

## Purpose

建立所有产品进入 AI TikTok Shop Operating System 时必须遵循的 Product Intelligence 标准流程。产品事实、视觉资料、来源和验证结论必须可追踪，禁止将 AI 推测写入 Product Profile。

## Required Stages

所有产品必须按顺序经过以下阶段，不得跳过前置阶段：

### 1. Product Intake

登记 Project、产品标识、目标市场、Owner、任务和已提供材料。未知字段保持未确认状态，不得推测补全。

### 2. Source Collection

按照来源优先级收集可追踪资料，将每个来源登记到 `PRODUCT_SOURCE_MAP.md`。只有完成必要来源登记后，才可进入 Fact Extraction。

### 3. Fact Extraction

从已登记来源提取原始事实，并记录对应来源、原文位置和验证状态。AI 推测、常识补全或无来源结论不得进入 Product Profile。

### 4. Visual Asset Extraction

从已登记且允许使用的来源提取产品视觉资料，保存资产位置、来源和状态，并写入 `PRODUCT_VISUAL_PROFILE.md`。

### 5. Verification

交叉核对产品事实与视觉资料，识别冲突、缺失和未验证内容，并将结果写入 `PRODUCT_VERIFICATION_REPORT.md`。

### 6. Product Profile Approval

审核 Product Profile、Source Map、Visual Profile 和 Verification Report。只有完成审核并明确批准的事实与视觉资料，才可进入下游流程。

## Source Collection Standard

来源按以下优先级使用：

### Level 1 — Owner Confirmed Information

由产品所有者明确确认的信息。

### Level 2 — Official Product Page

品牌或制造商维护的官方产品页面与官方资料。

### Level 3 — Marketplace Listing

Amazon、TikTok Shop 等 Marketplace Listing。必须记录具体 Listing 和采集时间，不得默认其内容等同于官方事实。

### Level 4 — Supplier Assets

供应商提供的产品文件、图片、包装资料和规格信息。

### Level 5 — Third-party Data

第三方网站、数据库、媒体或用户生成内容。只能作为补充来源，必须标记其验证状态。

当不同来源发生冲突时，优先级较高不代表自动正确；必须记录冲突并完成验证。禁止 AI 推测进入 Product Profile。

## Marketplace Identity Resolution

Marketplace URL 不等于单一产品身份。Amazon、TikTok Shop 和其他 Marketplace 来源必须先完成以下解析链：

`Parent Product → Variants → SKU → Selected Variant → Visual Match`

必须记录 Parent Product、可见 Variants、SKU 或平台标识、实际 Selected Variant，以及所选 Variant 与视觉资产是否匹配。禁止将页面默认 Variant 直接作为目标产品身份。

品牌相同不能证明不同 Variant 的颜色、尺寸、配置、配件、规格或视觉一致。任何无法解析到目标 Variant 的信息必须保持未验证状态。

## Owner Provided Marketplace Link

Owner 提供的 Marketplace 链接属于 `Trusted Source Reference`，但不等于已经确认的产品身份。

使用前必须解析：

- Variant
- SKU 或平台产品标识
- 产品版本

不得因为品牌相同而认定所有 Variant 一致。只有完成 Selected Variant 与目标产品的事实和视觉匹配后，链接内容才可用于对应 Product Profile。

## Amazon Deep Intelligence Protocol

Amazon Listing 不仅用于视觉图片。完成 Marketplace Identity Resolution 后，Product Intelligence 流程必须支持提取并验证以下信息。

### Product Identity

- Brand
- ASIN
- Parent ASIN
- Variant

### Product Facts

- Title
- Bullet Points
- Description
- Specifications
- Images
- Dimensions
- Accessories

### Customer Intelligence

- Rating
- Review Count
- Positive Review Patterns
- Negative Review Patterns
- Common Complaints
- Purchase Motivations

所有字段必须关联具体 ASIN、Selected Variant、来源位置和采集时间。评论模式必须来源于可追踪证据，不得将单条评论自动概括为普遍结论。

## Customer Intelligence

Customer Intelligence 用于保存可追踪的消费者反馈，不得替代 Product Truth。输出文件为 `CUSTOMER_INTELLIGENCE.md`，必须区分：

- Positive Signals
- Negative Signals
- Customer Language
- Purchase Motivation
- Usage Scenario

消费者原始表达、归纳模式和分析结论必须分开记录。每个结论必须保留 Evidence Source，并标记样本范围和验证状态。

## Purchase Objection Map

将已验证的 Customer Objection 连接到 Resolution Strategy 和 Suggested Content Angle。输出文件为 `PURCHASE_OBJECTION_MAP.md`。

Purchase Objection Map 只能使用 Customer Intelligence 中有证据支持的问题，不得根据 AI 推测创建消费者异议。

## Product Source Matrix

所有来源必须在 `PRODUCT_SOURCE_MATRIX.md` 中标明其系统角色，角色可包括：

- Product Truth
- Visual Source
- Customer Insight
- Market Signal
- Validation
- Content Insight

通用角色示例：

- Amazon：Product Truth、Visual Source、Customer Insight
- TikTok：Market Signal、Validation
- Kalodata：Market Signal、Content Insight

来源角色表示允许使用的情报范围，不代表该来源中的全部信息均已验证。

## Visual Asset Extraction Standard

每个产品必须检查并收集以下视觉资料：

- Product Main Image
- Product Detail Images
- Package Images
- Accessory Images
- Dimension Images

每项视觉资料必须记录来源、文件位置、提取日期、使用权限状态、与产品身份的一致性以及验证结果。缺失资产必须明确标记，不得使用推测或生成图替代已验证资料。

视觉资料输出文件：`PRODUCT_VISUAL_PROFILE.md`。

## Visual Asset Source Priority v1.1

视觉资产按以下优先级选择和验证：

### Level 1 — Owner Provided Assets

用户提供的图片、视频和供应商确认素材。

### Level 2 — Official Brand Assets

品牌官网和品牌官方发布的视觉素材。

### Level 3 — Amazon Listing Assets

Amazon ASIN 页面中的产品图片、详情图和尺寸图。用于产品视觉锁定；必须确认 Listing 与目标产品精确匹配。

### Level 4 — Kalodata Product Assets

TikTok Shop 生态数据来源，包括商品图片、商品封面和关联素材。用于补充 TikTok 生态视觉理解；必须记录具体来源和匹配状态。

### Level 5 — TikTok Shop Product Assets

TikTok 商品页面中的视觉素材。由于 Security Check、动态加载或页面限制，允许作为辅助来源，不得因页面不可访问而停止视觉采集。

### Level 6 — Supplier Assets

供应商提供且可追踪到目标产品的视觉素材。

### Level 7 — Third-party Assets

第三方参考素材，只能作为低置信度补充来源。

## Visual Source Fallback Rule

如果主来源不可访问，不得直接判定 `Visual Asset Unavailable`。必须记录访问失败，并继续尝试其他尚未检查的视觉来源。

示例回退路径：

`TikTok Shop unavailable → Amazon → Kalodata → Supplier`

只有完成适用来源的逐级尝试并记录结果后，才能将资产标记为不可用。

## Source Confidence

每个来源必须在 `PRODUCT_SOURCE_MAP.md` 中记录 `Source Confidence`：

- `High`：Owner、Official 或 Exact Marketplace Match。
- `Medium`：已经验证匹配的 ecosystem source。
- `Low`：Third-party reference。

Source Confidence 表示来源可信程度，不替代 Fact Verification、Visual Verification 或使用权限检查。

## Visual Conflict Resolution

不同来源的图片出现冲突时，必须记录 Conflict，禁止自动覆盖任何已记录资产或将其中一个版本自动设为已确认。

例如 Amazon 显示 Black、TikTok Shop 显示 White 时，必须记录来源、冲突属性和各版本证据，并将状态设为 `Waiting Owner Review`。只有 Owner Review 明确确认后，才能更新 Visual Lock 或批准相关视觉资产。

## Approval Gates

1. 未完成 Source Collection，不得进入 Fact Extraction。
2. 未完成 Fact Verification，不得批准 Product Profile。
3. 未完成 Visual Verification，不得进入 Video Production。
4. 未确认的信息必须保留在 Unverified Information，不得作为已确认事实使用。
5. Product Profile Approval 必须留下审核状态和审核记录。
6. Marketplace 来源未完成 Selected Variant 和 Visual Match，不得作为目标产品身份依据。
7. Customer Intelligence 与 Purchase Objection Map 必须保留证据来源，不得由 AI 推测填充。
