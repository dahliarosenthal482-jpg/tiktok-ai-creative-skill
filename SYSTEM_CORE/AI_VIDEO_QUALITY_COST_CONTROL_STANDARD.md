# AI Video Production Quality & Cost Control Framework v1.0

Task Type: SYSTEM_UPGRADE

Status: EXECUTED — WAITING SUPERVISOR REVIEW

Scope: Provider-neutral model selection, generation budgets, retry governance, immutable Prompt versions, quality scoring, and abstract production learning. This standard does not authorize real generation, provider access, credentials, automation, or project work.

Dependency: `SYSTEM_CORE/AI_VIDEO_PRODUCTION_PIPELINE_STANDARD.md`

## Control Sequence

`Approved Creative Production Specification → Generation Decision → Model Selection Decision → Budget Authorization → Prompt Version → Generation Attempt → Quality Review → Retry / Final Decision → Abstract Learning`

Generation is permitted only when both the Specification gate and Budget gate pass. Final Asset admission is permitted only when the Quality gate passes.

## 1. Model Selection Policy

Model selection occurs after Generation Decision and before a Generation Task enters `PROMPT_READY`.

Input: approved Creative Production Specification and Generation Decision.

Output: Model Selection Decision.

Required fields:

- Selection ID
- Generation Goal
- Required Quality Level
- Generation Type
- Selected Provider
- Selected Model
- Reason
- Alternative Option
- Risk

### Selection Priorities

- Product Fidelity Priority: favor capabilities that preserve approved geometry, color, packaging, components, and reference-image identity.
- Character Consistency Priority: favor capabilities that preserve an approved Role Lock across required outputs.
- Speed Priority: favor acceptable latency only after all mandatory fidelity and compliance requirements remain satisfiable.
- Cost Priority: minimize estimated cost within the required quality level; low cost cannot waive a hard quality gate.
- Creative Exploration Priority: permit broader variation only when the Specification explicitly authorizes exploration and Product/Role/Claim locks remain protected.

### Selection Rules

1. Random model selection is prohibited.
2. Every selection must map the Generation Goal and Required Quality Level to documented capabilities, constraints, estimated cost, and known risk.
3. Provider availability or popularity alone is not a sufficient reason.
4. The Alternative Option must remain viable under the same hard constraints or be marked unavailable with a reason.
5. If no candidate meets mandatory constraints and budget, selection status is `BLOCKED`; the Agent must not silently lower quality or change the Specification.
6. Provider and model names are decision outputs, not permanent Agent bindings. Calls remain behind Provider Adapters.

## 2. Generation Budget Control

Every generation scope requires an approved Budget Record before the first provider request.

Required fields:

- Budget ID
- Project/Task Scope
- Maximum Generation Count
- Maximum Retry Count
- Estimated Cost
- Actual Cost
- Approval Required

Additional control fields: Currency, Cost Unit, Approved By, Budget Status, Remaining Generation Count, Remaining Retry Count, and Stop Reason.

### Budget Rules

1. Estimated Cost must be recorded before authorization; Actual Cost is updated after every billable attempt.
2. Generation Count and Retry Count are independent controls. A retry consumes both a generation attempt and a retry allowance.
3. The lowest of financial budget, generation-count limit, and retry-count limit controls the stop decision.
4. Crossing or forecasting an overrun sets Budget Status to `STOPPED_BUDGET_EXCEEDED`; no further request may be sent without a new human approval record.
5. Unavailable price information sets `Approval Required: YES`; cost must not be assumed to be zero.
6. Confirmed non-billable Provider Errors still count toward operational retry limits; Actual Cost follows verified billing evidence.
7. Budget approval does not approve content, Prompt, provider credentials, or final assets.

### Automatic Retry Boundary

An automatic retry is allowed only when all conditions are true:

- the failure is a correctable Prompt-format or transient Provider Error;
- the correction does not change Product Lock, Role Lock, Scene Lock, claims, creative objective, or required quality;
- no more than one automatic correction has been attempted for the same failure chain;
- remaining generation, retry, and cost budgets are sufficient;
- the new Prompt version and correction reason are recorded before retry.

Human approval is required for Product Drift, Character Drift, altered product use, claim risk, ambiguous source assets, Specification changes, quality-level reduction, provider/model substitution outside the approved Alternative Option, or any budget overrun.

## 3. Generation Retry Policy

Every retry is a new, traceable attempt. Infinite regeneration is prohibited.

Required fields:

- Retry ID
- Original Task
- Failure Reason
- Failed Asset
- Correction Action
- New Version

Additional fields: Failure Class, Previous Prompt Version, New Prompt Version, Model Selection ID, Budget ID, Approval Reference, and Retry Status.

### Failure Classification

- Product Drift: product identity, geometry, color, packaging, control layout, accessory, or Product Lock failure.
- Character Drift: Role Lock or identity-continuity failure.
- Scene Failure: environment, action, use method, continuity, or physical-plausibility failure.
- Motion Failure: temporal distortion, unstable motion, impossible movement, or unusable action.
- Quality Failure: visual or technical output below the required quality level.
- Provider Error: provider-side request, capacity, processing, status, or delivery failure.

### Retry Decision

1. Classify the failure and preserve the failed asset before proposing a correction.
2. A retry must state exactly what changes and what remains locked.
3. Product Drift, Character Drift, and claim-related failures require human confirmation before retry.
4. A transient Provider Error may retry automatically once if the budget allows and no content input changes.
5. Repeated failure of the same class after the authorized correction stops the chain and requires review.
6. A retry creates a new Prompt version, task-attempt record, and output Asset ID.
7. A rejected output must not be overwritten, relabeled as approved, or used as a reference without explicit review permission.

## 4. Prompt Version Control

All Prompts are immutable versioned records. Overwriting Prompt content is prohibited.

Required fields:

- Prompt ID
- Task ID
- Version
- Created Time
- Change Reason
- Changed Section
- Previous Version
- Status

Version statuses: `Draft`, `Testing`, `Approved`, `Rejected`, and `Archived`.

### Version Rules

1. Prompt ID identifies the lineage; Version identifies one immutable record.
2. A changed field, lock, constraint, provider translation, or correction requires a new Version.
3. Every Version points to its Previous Version except the lineage root.
4. `Testing` does not authorize production unless the task and budget explicitly permit a test attempt.
5. Only an authorized reviewer may mark a version `Approved`; execution Agents may submit but not self-approve.
6. `Rejected` versions retain the Review reason. `Archived` versions remain readable but cannot start a new generation.
7. Generation records reference the exact Prompt ID and Version used; “latest” is not an acceptable production reference.
8. Prompt-learning comparisons must hold other relevant variables constant or disclose confounding changes.

## 5. AI Video Quality Evaluation

Every generated candidate receives a Quality Evaluation before Final Asset admission.

### Scored Dimensions

Each applicable dimension is scored from 0 to 5 with reviewer evidence:

- Product Fidelity
- Character Consistency
- Scene Consistency
- Motion Quality
- Visual Quality
- Claim Compliance
- Platform Style Fit

Score meanings:

- 0: absent, unusable, or severe violation.
- 1: major failure.
- 2: below requirement.
- 3: acceptable with visible limitations.
- 4: strong compliance.
- 5: fully meets the approved requirement with clear evidence.

Quality Score is the sum of applicable dimension scores divided by the maximum applicable score, multiplied by 100. A dimension may be `N/A` only when the Specification makes it genuinely inapplicable; the reviewer records the reason.

### Risk Level

- `LOW`: no hard-gate failure and only minor non-blocking limitations.
- `MEDIUM`: correctable limitations or uncertain evidence requiring revision or targeted review.
- `HIGH`: Product/Character/Scene integrity failure, claim risk, unusable technical defect, or missing provenance.

### Review Decision

- `APPROVED`: Quality Score is at least 80, every applicable dimension is at least 3, and all hard gates pass.
- `NEEDS_REVISION`: a correctable failure exists, the retry is authorized, and no prohibited content is approved for use.
- `REJECTED`: a hard-gate violation, unacceptable risk, repeated failed correction, missing provenance, or non-recoverable output exists.

Hard gates override the numeric score. Product Fidelity, Claim Compliance, source permission, Specification identity, and asset provenance must pass. Character Consistency and Scene Consistency are also hard gates when applicable. A high average cannot compensate for a hard-gate failure.

Required output fields: Quality Score, Dimension Scores and Evidence, Risk Level, Review Decision, Blocking Issues, and Required Correction.

## 6. Production Learning Loop

`Generated Asset → Quality Review → Failure Analysis → Prompt Improvement → Future Generation`

### Learning Rules

1. The source record remains in project scope; only an abstract, cross-project-safe lesson may be proposed for System Memory.
2. A lesson describes a reusable failure class, constraint pattern, decision rule, or review check—not a product, market, competitor, account, asset, Prompt, price, metric, or project strategy.
3. One failed or successful generation is an observation, not a universal rule.
4. A proposed lesson discloses model/provider version, changed variables, confounders, evidence count, and confidence without copying project data into system rules.
5. Promotion to a system rule requires independent review and explicit approval.
6. Learning must never weaken Product Lock, Role Lock, Scene Lock, Claim Compliance, source permission, budget, or Review Gate requirements.

## Governance and Prohibitions

- No video generation or video API call is authorized by this standard.
- No real Prompt, project case, provider account, credential, n8n workflow, or automation is created.
- No Agent may increase a budget, extend retries, lower quality, change approved locks, or approve its own output without the required authority.
- All decisions, costs, attempts, versions, assets, reviews, and risks must remain traceable in Git-managed project records when a future project task is authorized.
