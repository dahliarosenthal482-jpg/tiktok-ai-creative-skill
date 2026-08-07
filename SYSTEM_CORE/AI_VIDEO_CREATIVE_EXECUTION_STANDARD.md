# AI Video Creative Execution Framework v1.0

Task Type: SYSTEM_UPGRADE

Status: EXECUTED — WAITING SUPERVISOR REVIEW

Scope: Provider-neutral conversion of approved Creative Strategy into a reviewable Creative Production Specification and structured Video Production Input. This standard defines schemas and gates only. It does not authorize real scripts, Hook copy, Prompts, generation tasks, provider calls, or project execution.

Dependencies:

- `SYSTEM_CORE/AI_VIDEO_PRODUCTION_PIPELINE_STANDARD.md`
- `SYSTEM_CORE/AI_VIDEO_QUALITY_COST_CONTROL_STANDARD.md`

## 1. Creative Execution Flow

`Market Intelligence → Creative Strategy → Creative Production Specification → Creative Review Gate → Video Production Pipeline`

The Creative Production Specification is the only standard handoff from Creative Agent to Video Production Agent. Strategy documents, notes, content hypotheses, Script Frameworks, Scene Plans, and Prompt modules cannot independently authorize generation.

### Input Boundary

Creative Execution may use only approved, traceable inputs referenced by the authorized task. An input may guide structure but cannot silently become Product Truth, an approved claim, a production asset, or a proven creative result.

### Output Boundary

The output defines objectives, requirements, locks, references, and review status. It must not contain finished advertising copy, spoken lines, production-ready Prompts, generated assets, or provider commands unless a separately authorized downstream task explicitly permits them.

## 2. Creative Production Specification

### A. Basic Information

- Specification ID
- Market
- Product Reference
- Audience
- Video Objective

### B. Creative Objective

- Content Goal
- Attention Goal
- Interest Goal
- Desire Goal
- Action Goal

### C. Content Structure

- Content Type
- Story Structure
- Hook Objective
- Problem Introduction
- Product Introduction
- Demonstration Requirement
- Trust Element
- CTA Objective

### D. Production Controls

- Product Lock Reference
- Role Lock Reference
- Scene Planning Reference
- Camera Requirement
- Motion Requirement
- Claim Restriction Reference
- Platform Requirement
- Generation Constraint

### E. Governance

- Strategy Source Reference
- Evidence Boundary
- Version
- Created By
- Approval Status
- Approved By
- Review Report Reference
- Risk Items

### Specification Rules

1. Each field states an objective, boundary, requirement, or reference—not finished creative copy.
2. The Specification must trace every factual product statement and claim boundary to an approved source.
3. Content hypotheses remain hypotheses and must not be relabeled as validated performance.
4. The Specification is immutable after approval. Any material change creates a new version and requires a new Creative Review.
5. Missing required fields set the Specification to `INCOMPLETE`; a Generation Task cannot be created.
6. Creative Agent execution status does not equal Specification approval.

## 3. Script Framework

The Script Framework defines the logical jobs a future script must perform. It is not a script and cannot contain finished dialogue, narration, captions, titles, or Hook copy.

Required fields:

- Script Structure ID
- Opening Objective
- Main Message
- Proof Requirement
- Objection Handling
- Conversion Moment
- CTA Purpose

### Script Framework Rules

1. Opening Objective defines the attention job without wording the opening line.
2. Main Message identifies one approved communication priority without writing narration.
3. Proof Requirement specifies the type and source of proof needed; it cannot invent proof.
4. Objection Handling identifies the concern and permitted evidence boundary without drafting a response line.
5. Conversion Moment defines the decision-stage purpose without claiming causality.
6. CTA Purpose defines the intended action and compliance boundary without producing CTA copy.
7. A Script Framework must reference its Specification ID and cannot override Product Lock, claims, Audience, or Video Objective.

## 4. Scene Planning Framework

Scene Planning Schema defines what each future Scene must communicate and constrain. It is not a shot list, storyboard, camera command, or production-ready scene.

Each Scene record requires:

- Scene ID
- Scene Objective
- Duration Range
- Character Requirement
- Product Presence
- Environment
- Action Requirement
- Camera Requirement
- Transition Purpose

### Scene Planning Rules

1. Scene Objective maps to one approved Content Structure function.
2. Duration Range is a planning constraint, not a frame-accurate timeline.
3. Character Requirement references an approved Role Reference and does not invent identity traits.
4. Product Presence references the approved Product Lock and allowed visibility/use state.
5. Environment and Action Requirement must be physically plausible and claim-compliant.
6. Camera Requirement describes functional framing or movement needs, not provider syntax.
7. Transition Purpose describes narrative continuity, not a generated transition instruction.
8. Scene Plans remain planning records until Creative Review approves the full Specification.

## 5. Prompt Assembly Framework

Prompt Assembly converts approved Specification modules into a structured Prompt Contract. It defines module provenance and assembly order but does not contain or generate Prompt text.

### Modules and Sources

- Product Lock — source: approved Product Reference.
- Role Lock — source: approved Role Reference.
- Scene Lock — source: approved Scene Planning records.
- Camera Style — source: Creative Production Specification camera and style requirements.
- Motion Requirement — source: approved Scene action and motion requirements.
- Negative Constraint — source: Product, Role, Scene, Claim, platform, and generation restrictions.

### Assembly Rules

1. Every module records Source Reference, Source Version, Required/Optional status, and unresolved conflicts.
2. Assembly cannot add information missing from its approved source.
3. Product Lock, Role Lock, Scene Lock, Claim restrictions, and Negative Constraints cannot be weakened by Camera Style or Motion Requirement.
4. Conflicting modules block assembly and require Creative Review; later modules do not silently override earlier locks.
5. The assembled contract receives a Prompt ID and version under the Prompt Version System, but remains non-executable until all production admission gates pass.
6. Provider Adapters may translate syntax only; they cannot reinterpret creative objectives or locks.
7. No real Prompt example is part of this framework.

## 6. Creative Review Gate

The Creative Review Gate occurs before Model Selection, Budget Authorization, Prompt-ready status, and Generation Task creation.

Required checks:

- Strategy Alignment
- Product Truth
- Audience Match
- Content Goal
- Platform Fit
- Claim Compliance
- Production Feasibility

### Review Evidence

The reviewer must verify the Specification version, Strategy source, Product and Role references, Script Framework, Scene Planning records, claim restrictions, Prompt-module provenance, unresolved conflicts, and Risk Items.

### Decisions

- `APPROVED`: all required fields and hard gates pass; the exact Specification version may proceed to production admission checks.
- `NEEDS_REVISION`: correctable gaps exist; no Generation Task may be created until a revised version passes review.
- `REJECTED`: strategy conflict, invalid source, prohibited claim, infeasible production requirement, or non-recoverable boundary violation exists.

Execution Agents must not self-approve. Review approval applies only to the reviewed Specification version and does not approve a generated asset.

## 7. Video Production Admission Standard

Before a Generation Task can be created, all of the following are required:

- Creative Production Specification approved.
- Product Reference valid.
- Role Reference valid.
- Claim restriction confirmed.
- Generation Objective clear.

The following must also be traceable:

- exact Specification ID and version;
- Creative Review decision and reviewer;
- Script Structure ID;
- Scene Planning references;
- Prompt-module source references;
- Product, Role, Scene, and Negative Constraint locks;
- source and asset usage permission;
- unresolved Risk Items;
- Model Selection and Budget records when those downstream decisions have been made.

If any required condition is missing, invalid, conflicting, expired, or unapproved, admission status is `BLOCKED` and the Video Production Agent must not create a Generation Task.

## 8. Responsibility Boundary

### Creative Agent

- Creates and versions the Specification, Script Framework, Scene Planning Schema entries, and Prompt Assembly manifest.
- Preserves approved evidence and claim boundaries.
- Submits work as `EXECUTED`, not `APPROVED`.

### Creative Review Agent

- Independently validates the Creative Review Gate.
- Issues `APPROVED`, `NEEDS_REVISION`, or `REJECTED` for the exact Specification version.

### Video Production Agent

- Accepts only an admitted Specification.
- Must not repair missing creative approval by inventing content, references, claims, or locks.

## 9. Prohibitions

- No real script, Hook wording, spoken copy, advertising title, Prompt example, or generated asset is created by this standard.
- No video API, provider account, credential, n8n workflow, or automation is called or modified.
- No project instance, product fact, market signal, customer signal, video record, or Creative Strategy example may be copied into this system standard.
- Framework status is `EXECUTED — WAITING SUPERVISOR REVIEW`; it is not self-approved.
