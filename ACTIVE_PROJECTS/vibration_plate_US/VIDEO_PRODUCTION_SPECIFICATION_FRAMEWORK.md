# Video Production Specification Framework v1.0

Framework ID: VP-US-005C-R1-VPSF-v1.0

Task ID: VP-US-005C-R1

Executor: WORK-CREATIVE-001

Status: EXECUTED — WAITING SUPERVISOR REVIEW

Scope: Provider-neutral framework that converts an approved Script Package into reviewable AI video production requirements. It is the only formal production input accepted by WORK-VIDEO-001 after Creative Review approval. It contains no HTM-specific content, real script, spoken line, Hook wording, Storyboard, Shot List, Scene timeline, Prompt, provider request, API payload or Generation Task.

## Canonical architecture

`Creative Strategy → Script Package → Video Production Specification → Creative Review → WORK-VIDEO-001 → Generation Task`

|Layer|Responsibility|Output|Cannot Do|
|---|---|---|---|
|Creative Strategy|Define why production is needed: Market Goal, Audience Direction, Content Opportunity and Business Objective|Creative Strategy|Define script organization or production parameters|
|Script Package|Define how information is organized: objective, flow, Hook category, proof logic, objection handling and CTA purpose|Script Package Output Contract|Select provider/model, define camera parameters, create Prompt or contact WORK-VIDEO-001|
|Video Production Specification|Translate approved Script Package logic into bounded production requirements|Versioned Video Production Specification|Generate content, self-approve or create a Generation Task|
|Creative Review|Review the exact Video Production Specification version|APPROVED / NEEDS_REVISION / REJECTED|Approve unspecified future changes|
|WORK-VIDEO-001|Accept only an APPROVED Video Production Specification and perform separate production-admission checks|Generation Task only after all gates pass|Repair missing approval or change Strategy, Script, Product, Claim or evidence status|

# 1. Metadata

Every instance must contain:

|Field|Requirement|
|---|---|
|Specification ID|Stable unique identifier|
|Version|Immutable reviewed version; material change creates a new version|
|Source Script Package|Exact Script Package ID and version|
|Creative Strategy Reference|Exact approved Strategy source|
|Product Reference|Exact approved Product Truth source when a real instance is created|
|Market / Language|Inherited from approved sources; never inferred|
|Created By|Responsible Creative Agent|
|Approval Status|`DRAFT`, `INCOMPLETE`, `APPROVED`, `NEEDS_REVISION`, or `REJECTED`|
|Approved By|Authorized Creative Reviewer only|
|Review Reference|Controlling review record for the exact version|
|Admission Status|`BLOCKED` until approval and all downstream admission requirements pass|

Missing, invalid, conflicting or unapproved required metadata sets the instance to `INCOMPLETE` and `BLOCKED`.

# 2. Production Objective

Production Objective translates the approved Script Objective into a production job without changing its meaning.

Required fields:

- Primary Objective Type.
- Viewer Goal.
- Business Goal.
- Measurement Direction.
- Production Communication Goal.
- Required comprehension or decision outcome.
- Elements that must not be optimized at the expense of Product Truth, claims or audience alignment.

The Production Objective does not contain finished wording and cannot invent a new business objective.

# 3. Content Structure

Source: approved Script Package only.

Required fields:

- Source Script Structure ID.
- Content Type.
- Ordered Information Flow.
- Opening Objective and Hook Category.
- Context function.
- Problem / Desire function.
- Product-understanding function.
- Proof Logic and source reference.
- Objection-handling function and evidence boundary.
- CTA Purpose and verification requirement.
- Evidence classification for each function.

This section preserves logical content organization. It does not write a script, Hook sentence, Scene timeline or Shot List.

# 4. Production Requirement

This section defines AI production requirements derived from the approved content structure.

|Requirement|Definition|Boundary|
|---|---|---|
|Duration Requirement|Planning range or maximum/minimum needed to deliver the approved information flow|Not frame-accurate timing and not a proven performance rule|
|Visual Style Requirement|Overall visual treatment and authenticity level needed for the objective|Must not weaken Product/Role/Claim locks|
|Camera Requirement|Functional framing, stability, visibility and movement needs|No provider-specific syntax or unreviewed technical parameter|
|Environment Requirement|Physical setting, continuity and plausibility requirements|No invented location claim or unapproved context|
|Motion Requirement|Permitted subject/product movement and continuity constraints|No impossible, unsafe or unsupported behavior|
|Character Requirement|Whether a role is required and what approved reference class is needed|Identity-specific production blocked without approved Role Reference|
|Product Requirement|Required product visibility, interaction and fidelity priority|Must trace to approved Product Reference|
|Platform Requirement|Format, disclosure and style-fit requirements for the target platform|No fabricated native engagement or social proof|

Production requirements are provider-neutral and must not include Prompt text.

# 5. Product Lock

Every real instance must define:

- Approved Product Reference and source version.
- Product identity and allowed variant state.
- Visual identity, geometry, scale and component constraints.
- Approved packaging reference or explicit `PACKAGING NOT AUTHORIZED`.
- Permitted product presence and interaction state.
- Prohibited variant, component, feature, deformation and visual drift.
- Approved claim reference and factual feature boundary.

The framework adds no product fact. Missing Product Reference blocks the Specification.

# 6. Role Lock

Every instance must state either `NO ROLE` or provide:

- Approved Role Reference ID and version.
- Character Requirement and narrative function.
- Identity, face, body, wardrobe and age-presentation continuity.
- Allowed action and interaction boundaries.
- Prohibited identity drift, impersonation, body transformation, medical targeting and unapproved testimony.

A role-dependent Specification without a valid approved Role Reference is `INCOMPLETE` and `BLOCKED`.

# 7. Scene Requirement

Scene Requirement defines production inputs rather than a Storyboard or Shot List.

Required fields:

- Scene Planning Reference IDs.
- Scene function mapped to the approved Content Structure.
- Environment and continuity requirements.
- Product Presence requirement.
- Character presence requirement.
- Action and interaction boundaries.
- Functional camera requirement.
- Motion and transition purpose.
- Proof visibility requirement.
- Physical plausibility and safety boundary.
- Source permission and unresolved conflict status.

No scene record may add a script line, frame sequence, provider command or unsupported action.

# 8. Generation Constraint

Every instance must consolidate:

- Product Fidelity and prohibited visual drift.
- Role Fidelity and identity consistency.
- Scene continuity and physical plausibility.
- Claim restrictions and forbidden results.
- Platform compliance and disclosure requirements.
- Audience alignment and targeting limits.
- Source/asset permission restrictions.
- Negative Constraint list.
- Evidence-status preservation.
- Offer or time-sensitive fact verification requirements.
- Prohibited Prompt additions, unsupported features, fabricated proof and silent conflict resolution.

Conflicting constraints block the Specification and return it for revision.

# 9. Provider Adapter Input

This section defines a provider-neutral compatibility contract for future Kling, Omni, Seedance or Veo Adapter evaluation. It does not select a provider and contains no provider parameter or API payload.

|Field|Required Value|
|---|---|
|Required Capability Class|For example: product fidelity, reference-image support, role consistency, controlled motion or duration support as abstract capability needs|
|Reference Asset Types|Approved Product, Role and Scene reference classes required|
|Fidelity Priority|Relative priority among Product, Role, Scene, Motion and style fidelity|
|Duration Compatibility|Required supported duration range as an admission check|
|Aspect / Platform Compatibility|Required output-format capability without provider syntax|
|Constraint Preservation|Adapter must preserve all locks, claims and negative constraints|
|Unsupported Capability Response|Set admission to `BLOCKED`; do not weaken requirements|
|Compatibility Status|`UNASSESSED`, `COMPATIBLE`, `CONDITIONAL`, or `INCOMPATIBLE`|

Provider and model selection occur only in a separately authorized decision layer. Adapters may translate syntax but cannot reinterpret the Specification.

# 10. Review Gate

The exact Video Production Specification version must pass independent Creative Review before WORK-VIDEO-001 receives it.

## Required checks

- Creative Strategy alignment.
- Source Script Package identity and integrity.
- Production Objective fidelity.
- Content Structure preservation.
- Production feasibility.
- Product Lock and valid Product Reference.
- Role Lock and valid Role Reference when applicable.
- Scene requirements and physical plausibility.
- Claim and platform compliance.
- Source/asset permission.
- Provider-neutral compatibility requirements.
- Evidence classification and unresolved Risk Items.

## Decisions

- `APPROVED`: the exact version may be sent to WORK-VIDEO-001 for separate production admission. Approval does not itself create a Generation Task.
- `NEEDS_REVISION`: return to WORK-CREATIVE-001; WORK-VIDEO-001 handoff is prohibited.
- `REJECTED`: stop the pipeline for this version.

## WORK-VIDEO-001 admission rule

WORK-VIDEO-001 accepts only an `APPROVED` Video Production Specification. Before creating a Generation Task it must also verify valid references, claim restrictions, source permissions, clear objective, model-selection record, budget authorization, Prompt Contract readiness and all applicable production gates. Any missing condition sets admission to `BLOCKED`.

## Evidence Boundary

### Observed Evidence

- Supervisor Review `60fbd0f9068d7be4002a429c6f299298b9d78fcd` identifies the missing post-Script Video Production Specification and requires it as the final production contract.
- Existing system and project records require versioned sources, independent review, Product/Role/Scene locks, claim restrictions and blocked admission when required inputs are missing.

### Inference

- Separating content organization from production requirements can reduce authority ambiguity and prevent production parameters from leaking into Script Packages.

### Future Test Direction

- Validate field completeness through separately authorized, non-production test instances before adopting workflow changes beyond this project.

## Risk Items

- This is a framework, not an approved populated Video Production Specification.
- No role-dependent production may proceed without an approved Role Reference.
- Packaging proof remains blocked without an approved packaging reference.
- Video Intelligence remains `PARTIAL COMPLETE`, Quality A = 0; no Hook, Scene, character, camera style, duration or CTA is proven.
- Provider compatibility remains abstract and unassessed; no provider or model is selected.
- Model selection, budget authorization, Prompt Contract and Generation Task remain separate downstream requirements.
