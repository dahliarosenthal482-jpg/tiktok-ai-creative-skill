# AI Video Production Pipeline Framework v1.0

Status: EXECUTED — WAITING SUPERVISOR REVIEW

Scope: Cross-project governance, contracts, lifecycle, provider abstraction, asset traceability, and quality gates for future AI video production. This standard does not authorize a generation task, provider call, prompt example, or project production activity.

Quality and cost controls for model selection, generation budgets, retry limits, Prompt versions, scoring, and production learning are defined in `SYSTEM_CORE/AI_VIDEO_QUALITY_COST_CONTROL_STANDARD.md`.

The standard conversion from Creative Strategy to an approved Creative Production Specification and Video Production Input is defined in `SYSTEM_CORE/AI_VIDEO_CREATIVE_EXECUTION_STANDARD.md`.

## Pipeline Architecture

`Market Intelligence Agent → Creative Production Agent → Video Production Agent → Review Agent`

1. Market Intelligence Agent supplies approved, evidence-bounded intelligence.
2. Creative Production Agent converts approved inputs into one Creative Production Specification.
3. Video Production Agent uses the approved Specification, Generation Decision Engine, and Provider Adapter layer to execute an authorized Generation Task.
4. Review Agent independently checks the output and controls admission to Final Asset status.

Every handoff must preserve source references, approval state, Agent identity, Task identity, Specification version, Prompt version, asset versions, Evidence Summary, and Risk Items.

## Agent Responsibilities

### Market Intelligence Agent

- Produces approved intelligence and separates Observed Evidence, Inference, and Future Test Direction.
- Does not create Generation Tasks or approve production specifications.

### Creative Production Agent

- Creates and versions the Creative Production Specification.
- Resolves creative intent into constraints without inventing Product Truth, claims, roles, or assets.
- Submits the Specification for approval and must not self-approve.

### Video Production Agent

- Creates a Generation Task only from an approved Specification.
- Records the Generation Decision, Prompt Contract version, Provider Adapter, reference assets, outputs, provider status, and failures.
- Must not bypass the Adapter layer or mark generated assets as finally approved.

### Review Agent

- Independently validates Specification compliance, asset provenance, consistency, claim compliance, and technical quality.
- Is the only role authorized to issue the final Review Result for a generated asset.

## Creative Production Specification

The Creative Production Specification is the single authorized input to video generation. Its canonical template is `ACTIVE_PROJECTS/_TEMPLATE/CREATIVE_PRODUCTION_SPECIFICATION.md`.

Required fields:

- Basic: Specification ID, Market, Product Reference, Target Customer, Video Goal, Content Type.
- Creative: Content Angle, Emotional Objective, Audience Trigger, Conversion Objective.
- Production: Style Requirement, Camera Style, Scene Requirement, Product Lock, Role Lock, Generation Constraint.
- Approval: Source Reference, Approval Status, Approved By.

No Generation Task may enter `PLANNING` unless the referenced Specification exists, is versioned, has traceable approved sources, and has `Approval Status: APPROVED` issued by an authorized reviewer. Missing or self-issued approval is a blocking failure.

## Video Generation Task

The canonical task template is `ACTIVE_PROJECTS/_TEMPLATE/VIDEO_GENERATION_TASK.md`.

Required fields: Generation Task ID, Input Specification ID, Generation Type, Provider, Model, Version, Prompt Version, Reference Assets, Output Assets, Status, and Review Status.

Lifecycle:

`CREATED → PLANNING → PROMPT_READY → GENERATING → GENERATED → QUALITY_CHECK → APPROVED / REJECTED`

Rules:

- Transitions must record timestamp, responsible Agent, evidence, and reason.
- `PROMPT_READY` requires a valid Prompt Contract and resolvable approved reference assets.
- `GENERATING` requires an authorized provider route and must never be inferred from a queued task.
- `GENERATED` means an output exists; it does not mean the output passed review.
- Only the Review Agent may transition from `QUALITY_CHECK` to `APPROVED` or `REJECTED`.
- Failed, cancelled, or expired attempts remain auditable and must not overwrite earlier versions.

## Generation Decision Engine

Input: approved Creative Production Specification.

Output: Generation Decision containing `generation_type`, reason, required references, fidelity priority, constraints, and compatible adapter capability.

Supported decision types:

- Image To Video
- Text To Video
- Character Consistency
- Product Demonstration

Decision rules:

- Prefer the method that satisfies approved fidelity and evidence constraints with the least unsupported invention.
- Product-identity priority requires approved visual references and Product Lock enforcement.
- Character Consistency requires an approved Role Reference and Role Lock.
- Product Demonstration requires verified usage boundaries and cannot invent operation or results.
- The decision selects capabilities, not a provider API.

The Decision Engine must not contain credentials, direct API calls, or provider-specific request payloads.

## Provider Adapter Architecture

`Video Production Agent → Generation Decision Engine → Provider Adapter → API Provider`

Adapter families may include Kling Adapter, Omni Adapter, Seedance Adapter, and Veo Adapter. Their presence here does not mean an implementation or provider is approved or available.

Every Adapter is responsible for:

- API parameter translation;
- provider authentication isolation;
- authorized request submission and status queries;
- provider state, error, metadata, and output normalization;
- returning asset provenance without changing creative meaning or approval state.

Agents must not bind directly to a model or provider API. Provider-specific fields remain inside the Adapter; shared contracts and states remain provider-neutral.

## Prompt Contract

The Prompt Contract is a structured, versioned production input and cannot add facts.

### Product Lock

Source: approved Product Reference. Constraints cover appearance, packaging, dimensional proportions, color, approved components, and prohibited variants or features.

### Role Lock

Source: approved Role Reference. Constraints cover identity continuity and allowed presentation boundaries. Without an approved Role Reference, identity-specific generation is blocked.

### Scene Lock

Constraints cover environment, action, use method, spatial continuity, and physical plausibility.

### Camera Style

Camera Style is variable. Native UGC may request smartphone-camera character, natural handheld movement, and realistic lighting, but no style is mandatory for every video.

### Negative Constraint

Must cover product deformation, identity drift, unsupported claims, unrealistic transformation, and prohibited variants, accessories, actions, or visual changes where applicable.

Contract rules:

- Prompt Version becomes immutable when generation begins; revisions create a new version.
- Every Prompt Contract references its Specification ID and approved assets.
- Provider translation must not delete locks, weaken negative constraints, or add unsupported claims.
- This standard defines fields only and contains no production prompt example.

## Video Asset Registry

The canonical template is `ACTIVE_PROJECTS/_TEMPLATE/VIDEO_ASSET_REGISTRY.md`.

Required fields: Asset ID, Generation Task ID, Asset Type, Version, Source, Created Time, Status, and Review Result.

Supported asset types include Generated Video, Keyframe, Reference Image, and Prompt Version.

- Every asset requires a stable ID and provenance.
- New versions are immutable records; reviewed assets cannot be silently overwritten.
- Asset Status and Review Result are separate.
- Only an asset that passes the Review Gate may become `FINAL_ASSET`.
- Rejected and superseded assets remain traceable with reason and parent version.

## Review Gate

The canonical template is `ACTIVE_PROJECTS/_TEMPLATE/VIDEO_QUALITY_REVIEW.md`.

Every generated candidate enters `QUALITY_CHECK` and is evaluated for Product Consistency, Character Consistency, Scene Consistency, Claim Compliance, and Technical Quality.

The Review Agent also verifies Specification ID, Prompt Version, reference assets, output checksum/location, provider metadata, and unresolved Risk Items.

Review Result is `APPROVED`, `NEEDS_REVISION`, or `REJECTED`. A candidate that has not passed the gate must not enter Final Asset status or downstream publication. Work execution feedback is not final approval.

## Data and Security Boundaries

- System standards contain reusable contracts and rules only; project facts and assets remain in the corresponding project workspace.
- Provider credentials must never be stored in Specifications, prompts, Generation Tasks, asset registries, execution logs, or Git history.
- Source and usage permission must be known before an asset is used as a generation reference.
- No real generation begins merely because this framework or a template exists.
