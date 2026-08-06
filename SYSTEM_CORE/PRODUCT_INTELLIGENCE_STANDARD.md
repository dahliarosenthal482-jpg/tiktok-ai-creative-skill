# Product Intelligence Standard v1.1

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
