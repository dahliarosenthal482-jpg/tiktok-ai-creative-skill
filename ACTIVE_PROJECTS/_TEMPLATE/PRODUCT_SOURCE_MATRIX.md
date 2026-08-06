# Product Source Matrix

Project:

Product:

## Source Role Values

- Product Truth
- Visual Source
- Customer Insight
- Market Signal
- Validation
- Content Insight

## Source Entry Template

Source ID:

Source Type:

Source Role:

Evidence:

Information Covered:

Confidence:

Status:

## Schema Validation Rule

每个 Source Entry 必须严格按照以下固定顺序填写：

1. Source ID
2. Source Type
3. Source Role
4. Evidence
5. Information Covered
6. Confidence
7. Status

禁止将一个 Source 的字段放入另一个 Source Entry，禁止跨 Source 字段错位。缺失值必须填写 `None` 或明确状态，不得通过省略字段改变结构。

## General Role Examples

- Amazon: Product Truth, Visual Source, Customer Insight
- TikTok: Market Signal, Validation
- Kalodata: Market Signal, Content Insight
