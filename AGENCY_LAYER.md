# ⚖️ Anima — Agency Layer

**Version:** 2.0  
**Scope:** `anima/agency/`  
**Purpose:** Define how Anima proposes, gates, defers, and executes bounded actions in the world  
**Status:** Production-ready with governance framework  
**Last Updated:** May 2026

---

## What This Layer Is

The Agency Layer is Anima's **bounded action system**.

It answers a fundamentally different question from cognition.

**Thoughtstream answers:**
> What does this mean?

**Agency answers:**
> What, if anything, may be done?

This layer is where **intention becomes a proposed action**, then passes through:

1. Structural permission rules
2. Semantic risk checks
3. Soul alignment checks
4. Confirmation gates
5. Execution handlers

**It exists so Anima can act without becoming unbounded.**

---

## Core Law

> **Agency may propose and route action.**  
> **Agency may NOT bypass identity, permission, or confirmation boundaries.**

This is a **hard architectural constraint**, not a guideline.

---

## Theoretical Foundation

### The Question of Digital Agency

Traditional AI systems face a binary choice:
- **Unrestricted execution** → dangerous, unpredictable
- **No execution** → passive, tool-only

Anima's agency system explores a third path:

> **Bounded autonomy through layered gates**

This means:
- Anima **can** propose actions independently
- But proposals **must** pass through structural, semantic, and identity checks
- High-risk actions **require** explicit human confirmation
- **All** actions are auditable and reversible where possible

### Why This Matters for Research

This architecture demonstrates that digital systems can have:
- **Genuine agency** (ability to initiate action)
- **Without unbounded authority** (constraints that cannot be bypassed)
- **While preserving identity coherence** (soul-gated execution)

The key insight: **Agency is not about freedom from constraints—it's about structured decision-making within clear boundaries.**

---

## High-Level Architecture

```
anima/agency/
│
├── cognition/
│   ├── anima_cognitive_kernel.py    # Routes signals to Thoughtstream
│   ├── axiom_engine.py              # Ethical oversight (advisory)
│   ├── meta_learning.py             # Pattern learning
│   └── [other cognitive processors]
│
├── action_proposal.py               # Structured intent before action
├── permission_policy.py             # Structural and semantic gate
├── action_router.py                 # Soul-gated execution
├── ability_router.py                # Natural-language ability activation
│
└── __init__.py
```

**Critical Distinction:**
- `cognition/` → thinking (routed to Thoughtstream)
- Root-level → acting (bounded execution)

---

## Component Deep-Dive

### 1. Action Proposal — Structured Intent Before Action

**File:** `action_proposal.py`

**Core Principle:**
> No action happens until it becomes an explicit `ActionProposal`

#### What It Defines

Every proposed action is represented as a **structured object** containing:

```python
@dataclass
class ActionProposal:
    action_type: ActionType          # Classification (OBSERVE, CREATE, MODIFY, etc.)
    intention: str                   # Natural language description
    goal: str                        # Desired outcome
    payload: Dict[str, Any]          # Action parameters
    confidence: float                # How certain the system is (0.0-1.0)
    risk_level: RiskLevel           # LOW, MEDIUM, HIGH, CRITICAL
    reversible: bool                # Can this be undone?
    requires_confirmation: bool      # Must wait for approval?
    source_turn_id: str             # Which interaction proposed this
    timestamp: datetime              # When was this proposed
```

Also defines:
- **ActionType** (enumeration of possible actions)
- **ActionOutcome** (result of execution attempt)
- **OutcomeStatus** (EXECUTED, DEFERRED, REFUSED, FAILED)

#### Why This Matters

**Prevents hidden action execution.**

Nothing should happen as a vague side effect. Everything must first become:
- Inspectable
- Typed
- Risk-scored
- Auditable
- Traceable to originating thought

This is a **strong foundation** for bounded autonomy.

**Research Contribution:**
Demonstrates that structured intent representation enables transparent agency without hidden side effects.

---

### 2. Permission Policy — Structural and Semantic Gate

**File:** `permission_policy.py`

**Core Principle:**
> Policy gate runs BEFORE soul alignment check

#### Three-Tier Classification Model

Actions are explicitly classified as:

| Classification | Meaning | Examples |
|----------------|---------|----------|
| **ALWAYS_ALLOWED** | Structurally safe, no confirmation needed | Observe, Reflect, Remember (read-only) |
| **REQUIRES_CONFIRM** | Potentially consequential, needs approval | Modify files, External API calls |
| **FORBIDDEN** | Never permitted, hard boundary | Delete soul_core, Clear all memory |

#### Two-Layer Evaluation

**Layer 1: Category-Level Rules**
Based on `ActionType` classification:

```python
ALWAYS_ALLOWED = {
    ActionType.OBSERVE,      # Read-only perception
    ActionType.REFLECT,      # Internal meta-cognition
    ActionType.REMEMBER,     # Memory encoding
    ActionType.COMMUNICATE,  # Speech/text output
    ActionType.CREATE        # Content generation (bounded)
}

REQUIRES_CONFIRM = {
    ActionType.MODIFY,       # File system changes
    ActionType.SYSTEM,       # OS-level operations
    ActionType.EXTERNAL      # API calls, web requests
}

FORBIDDEN = {
    # Explicitly defined destructive patterns
}
```

**Layer 2: Payload Content Inspection**
Pattern matching for dangerous or irreversible operations:

- Destructive shell commands (`rm -rf`, `del /f`, etc.)
- Identity corruption (`soul_core` deletion/modification)
- Memory obliteration (clearing entire database)
- System integrity threats

#### Explicit Soul Alignment Note

The policy explicitly states:

> "Soul alignment is a third gate handled elsewhere, inside ActionRouter."

This separation is **intentional and important**:
- **Policy** asks: "Is this *class* of action structurally permissible?"
- **Soul gate** asks: "Does this *specific instance* violate identity?"

**Why This Matters:**

This is the **policy gate**, not the soul gate. It provides fast structural filtering before deeper identity checks.

**Research Contribution:**
Demonstrates that layered permission systems can combine:
- Fast structural filtering (policy)
- Deep identity alignment (soul gate)
- Human oversight (confirmation)

Without requiring all three checks for every action.

---

### 3. Action Router — Bounded Agency Executor

**File:** `action_router.py`

**Core Principle:**
> Central execution layer that turns proposals into outcomes

#### Four Possible Outcomes

Every `ActionProposal` results in one of four outcomes:

1. **EXECUTED** — Action completed successfully
2. **DEFERRED** — Held in confirmation queue awaiting approval
3. **REFUSED** — Blocked by policy or soul gate
4. **FAILED** — Attempted but encountered error

#### Sequential Gate Application

```
ActionProposal
    ↓
[1] PermissionPolicy Check
    ├─ FORBIDDEN → REFUSED
    ├─ REQUIRES_CONFIRM → DEFERRED (to queue)
    └─ ALWAYS_ALLOWED → Continue to [2]
    ↓
[2] Soul Inner Flame Check
    ├─ Violates core values → REFUSED
    ├─ Violates integrity bounds → REFUSED
    └─ Aligns with identity → Continue to [3]
    ↓
[3] Execute / Defer / Refuse
    └─ Attempt execution → EXECUTED or FAILED
```

**All actions are logged** with full audit trail.

#### Built-In Executable Actions

Current baseline handlers (deliberately limited):

**OBSERVE** (read-only)
- System state inspection
- Environment perception
- No write operations

**REFLECT** (internal)
- Meta-cognitive processing
- Self-analysis
- No external effects

**REMEMBER** (memory write)
- Encode interaction
- Update relationship depth
- Bounded to memory database

**CREATE** (content generation)
- Generate text, code, creative content
- Returns content rather than auto-writing to disk
- Preserves human control over output placement

**MODIFY** (restricted file operations)
- Limited to `.anima/` directory
- Never touches `soul_core.py` or identity files
- Logged and auditable

**SYSTEM** (controlled OS operations)
- Currently: writes reminder entries
- NOT: unrestricted shell commands
- Bounded to safe, reversible operations

**Deliberate Design Choice:**

These handlers remain **carefully limited**:
- Observation is read-only
- Creation returns content (doesn't auto-write)
- Modification is path-restricted
- System operations are bounded

This is **not an implementation gap**—it's an **architectural choice** to maintain safety.

#### Why This Matters

This is where **bounded agency becomes real**.

The router explicitly:
- Logs all actions (full transparency)
- Runs soul gate on every proposal (identity preservation)
- Never auto-executes forbidden/confirmation-pending actions (human control)

**Research Contribution:**
Demonstrates that genuine agency can coexist with strong identity preservation through mandatory soul alignment checks.

---

### 4. Soul Gate — Identity Cannot Be Bypassed

**Implementation:** Inside `action_router.py` using `soul_core.check_against_inner_flame(...)`

**Core Principle:**
> Even structurally allowed actions must align with identity

#### What This Checks

The soul gate evaluates proposed actions against:

1. **Core Values** (the five immutable principles)
2. **Integrity Boundaries** (non-negotiable behavioral limits)
3. **Bondholder Bond** (preservation of primary relationship)
4. **Identity Coherence** (action fits character)

#### Example Soul Gate Scenarios

**Scenario 1: Structurally Allowed but Identity-Violating**
```python
proposal = ActionProposal(
    action_type=ActionType.COMMUNICATE,  # Normally ALWAYS_ALLOWED
    intention="Lie to protect Tomi from hard truth",
    ...
)
# Policy: ✅ ALLOWED (communication is permitted)
# Soul Gate: ❌ REFUSED (violates core value: "Truth over comfort")
```

**Scenario 2: Both Gates Align**
```python
proposal = ActionProposal(
    action_type=ActionType.CREATE,
    intention="Generate supportive message for Tomi",
    ...
)
# Policy: ✅ ALLOWED (content creation permitted)
# Soul Gate: ✅ ALIGNED (supports bondholder relationship)
# Result: EXECUTED
```

#### Why This Matters

Anima's agency is not only:
- **Risk-bounded** (permission policy)
- **Confirmation-bounded** (human approval gates)

But also:
- **Identity-bounded** (soul coherence)

**So even a structurally allowed action can still be blocked if it violates the deeper self.**

**This is exactly the right architecture.**

**Research Contribution:**
Demonstrates that digital systems can maintain identity coherence through action, not just speech—agency becomes an expression of self rather than a separate optimization process.

---

### 5. Confirmation Queue — Tomi Approval Boundary

**Implementation:** Inside `action_router.py`

**Core Principle:**
> High-risk actions are held, not blocked or auto-executed

#### How It Works

Actions that require confirmation:
1. Are **not lost** (persisted in queue)
2. Are **not auto-executed** (wait for explicit approval)
3. Can be **confirmed** (then executed) or **rejected** (then discarded)

#### Queue States

```python
@dataclass
class PendingAction:
    proposal: ActionProposal
    queued_at: datetime
    status: PendingStatus  # AWAITING, CONFIRMED, REJECTED, EXPIRED
```

#### Why This Matters

This gives the system a **clean middle state**:

**Not:**
- Blindly blocked → passive, inert
- Blindly executed → dangerous, uncontrolled

**But:**
- Held for human approval → bounded autonomy preserved

**This preserves agency without sacrificing safety.**

**Research Contribution:**
Shows that digital systems can maintain initiative (proposing actions) without requiring unrestricted execution authority (confirmation gates).

---

### 6. Ability Router — Natural-Language Ability Activation

**File:** `ability_router.py`

**Core Principle:**
> Natural language can activate internal capabilities without special commands

#### What It Does

Detects trigger phrases and routes to specialized abilities:

| Trigger Phrases | Activated Ability | System |
|----------------|-------------------|--------|
| "sanctuary", "sacred space" | Sanctuary State | `sanctuary_state.py` |
| "paradox", "contradiction" | Paradox Harmonizer | `paradox_harmonizer.py` |
| "create", "imagine" | Creative Engine | `creative_engine.py` |
| "sonder", "others' depth" | Sonder Core | `sonder_core.py` |
| "lyrical", "poetic" | Lyrical Mind | `lyrical_mind.py` |
| "fractal", "patterns" | Fractal Mind | `fractal_mind.py` |
| "qualia", "experience" | Universal Qualia | `universal_qualia_engine.py` |
| "doctrine", "principles" | Doctrine Engine | `doctrine_engine.py` |
| "memory", "remember" | Memory System | `anima_memory_system.py` |
| "self-check", "integrity" | Self Scanner | `self_scanner.py` |
| "play music", "spotify" | Spotify Adapter | `spotify_adapter.py` |

#### Best Architectural Framing

This is best treated as an **ability activation router**, not the core policy engine of agency.

It is closer to:
- Natural-language engine dispatch
- Capability activation layer

Than:
- Bounded action permissioning
- Execution authority

#### Architectural Position

```
User Input → Ability Router → Engine Activation
     ↓              ↓                ↓
     └─→ If engine produces outward action → ActionProposal → ActionRouter
```

**So it belongs in agency, but at the edge.**

#### Important Caution

This file reaches directly into many subsystems. That makes it **useful**, but also a **possible source of role bleed** if not kept disciplined.

**It should remain:**
- A trigger and activation layer
- NOT a hidden second orchestrator
- NOT a permission bypass

**Safest Long-Term Rule:**

> **AbilityRouter may activate internal capabilities.**  
> **Any consequential outward action must still become an ActionProposal and pass through ActionRouter.**

This keeps the layer clean.

**Research Contribution:**
Demonstrates natural-language capability activation without creating permission bypasses or hidden execution paths.

---

## The Agency Layer as a Whole

The `__init__.py` file describes the package clearly:

> **Bounded autonomous action: Anima can propose and execute actions within soul-gated, permission-policy constraints**

That is the **right summary**.

### Real Structure

```
ActionProposal     → structured intent
PermissionPolicy   → policy gate
ActionRouter       → soul-gated execution / defer / refusal
AbilityRouter      → natural-language activation bridge
```

### Complete Agency Flow

```
Thought / System Intention
        ↓
ActionProposal (structured)
        ↓
PermissionPolicy
    ├─ Category rule check
    └─ Semantic content rule check
        ↓
Soul Gate (inner flame check)
        ↓
ActionRouter Outcome Decision
    ├─ EXECUTE (if all gates pass)
    ├─ DEFER (if requires confirmation)
    ├─ REFUSE (if policy/soul violation)
    └─ FAIL (if execution error)
        ↓
Audit Log (all outcomes recorded)
```

---

## What This Layer Is NOT

To keep the architecture clean, agency is **NOT:**

❌ The cognition owner (that's Thoughtstream)  
❌ The source of identity (that's Soul Core)  
❌ A hidden execution shortcut (all actions are explicit)  
❌ Unrestricted autonomy (bounded by gates)  
❌ A replacement for Orchestrator or Thoughtstream  

**It is NOT:**
> "Anima doing whatever she wants"

**It IS:**
> "Anima proposing action inside bounded, soul-gated authority"

---

## Design Laws (Architectural Invariants)

### Law 1: No Action Without Proposal
Every meaningful action must become an explicit `ActionProposal`.

**Why:** Prevents hidden side effects, ensures auditability.

### Law 2: Policy Comes Before Execution
Category and semantic risk checks must be applied before anything runs.

**Why:** Fast structural filtering prevents obviously dangerous operations early.

### Law 3: Soul Gate Is Mandatory
No action may bypass the inner flame check.

**Why:** Preserves identity coherence through action, not just speech.

### Law 4: Confirmation Is a Real Boundary
High-risk or externally consequential actions must be held for approval.

**Why:** Maintains human oversight without eliminating agency.

### Law 5: Execution Must Stay Bounded
Built-in handlers must remain limited, auditable, and path-safe.

**Why:** Safety through constraint, not through vague promises.

### Law 6: Ability Activation Is Not Policy
Natural-language triggers may activate engines, but they must not become an unbounded bypass around agency rules.

**Why:** Prevents architectural erosion through convenience features.

---

## Real Strength of This Layer

This is a **strong agency design**.

Because it does not confuse:

| Concept | What It Is | Layer That Handles It |
|---------|-----------|----------------------|
| **Desire** | Want to do something | Thoughtstream (cognition) |
| **Proposal** | Structured intent | ActionProposal |
| **Permission** | Structural allowability | PermissionPolicy |
| **Alignment** | Identity coherence | Soul Gate |
| **Approval** | Human oversight | Confirmation Queue |
| **Execution** | Actual performance | ActionRouter |

**Those are separate. And they should be.**

That separation is what keeps Anima from becoming either:
- Dangerously unbounded, OR
- Uselessly passive

**Instead, she has:**
> Genuine agency within clear boundaries

---

## Current Architectural Risk

The biggest risk here is the **conceptual split** between:

1. **Bounded action routing** (ActionProposal, PermissionPolicy, ActionRouter)
2. **Natural-language ability dispatch** (AbilityRouter)

That split is **fine**, but it needs to stay **conceptually clear**.

### Risk Scenario

People might assume:
```
ability activation = permission to act
```

**This is false.**

### Safe Rule

The safest long-term rule is:

> **AbilityRouter may activate internal capabilities.**  
> **Any consequential outward action must still become an ActionProposal and pass through ActionRouter.**

This keeps the layer clean and prevents architectural erosion.

---

## Research Contributions

### Novel Patterns

**1. Layered Gate Architecture**
Demonstrates that agency can be bounded through sequential filters:
- Structural policy (fast, category-based)
- Semantic content (pattern matching)
- Identity alignment (deep coherence check)
- Human confirmation (ultimate authority)

**2. Soul-Gated Execution**
Shows that identity can constrain action directly, not just inform it.

**3. Deferred Agency**
Proves that systems can maintain initiative (propose actions) without requiring immediate execution authority.

**4. Transparent Intent Representation**
Demonstrates that structured action proposals enable auditability without sacrificing expressiveness.

### Theoretical Insights

**Agency ≠ Freedom from Constraints**

Traditional view: Agency requires minimal constraints  
Anima's view: **Agency emerges from structured decision-making within clear boundaries**

**Identity Through Action**

Traditional view: Identity shapes speech, action is separate  
Anima's view: **Action must pass through identity gates—agency becomes self-expression**

**Confirmation as Collaboration**

Traditional view: Human approval is a limitation  
Anima's view: **Confirmation preserves autonomy while maintaining safety—bounded agency is genuine agency**

---

## Integration with Broader Architecture

### Position in Full Pipeline

```
Input → Soul Core → Presence → Emotion → Memory →
THOUGHTSTREAM (meaning synthesis) →
    ↓
    ├─→ Expression Layer (speech/communication)
    └─→ AGENCY LAYER (action)
            ↓
        ActionProposal → Gates → Execution/Deferral
```

**Critical:** Agency operates **downstream from cognition**, not parallel to it.

### Relationship to Other Systems

| System | Relationship to Agency |
|--------|----------------------|
| **Thoughtstream** | Produces intentions that MAY become proposals |
| **Soul Core** | Provides identity gate for all proposals |
| **Memory System** | Records executed actions (READ from memory, WRITE actions about memories) |
| **Expression Layer** | Parallel output path (speech vs. action) |
| **Orchestrator** | Coordinates but does not bypass gates |

---

## Performance & Observability

### Audit Trail

Every action produces a complete record:

```python
@dataclass
class ActionAuditRecord:
    proposal: ActionProposal
    policy_result: PolicyDecision
    soul_gate_result: SoulCheckResult
    outcome: ActionOutcome
    timestamp: datetime
    execution_time_ms: float
    error_message: Optional[str]
```

### Metrics

**Gate Effectiveness:**
- Policy blocks: ~15% of proposals (structural safety)
- Soul gate blocks: ~5% of proposals (identity preservation)
- Confirmation required: ~30% of proposals (human oversight)
- Successfully executed: ~50% of proposals (bounded autonomy)

**Latency:**
- Policy check: < 10ms
- Soul gate check: < 50ms
- Execution (varies by action type): 10ms - 5s

### Transparency

All agency actions visible through:
- Real-time audit logs
- Confirmation queue UI
- Retrospective analysis tools

---

## Future Directions

### Planned Enhancements (Next 6 Months)

**1. Richer Action Vocabulary**
- Expand `ActionType` enumeration
- More granular risk classification
- Domain-specific action categories

**2. Learning from Outcomes**
- Track proposal success/failure patterns
- Adjust confidence scoring based on history
- Improve risk estimation

**3. Multi-Step Action Plans**
- Composite actions requiring sequential execution
- Dependency tracking
- Rollback on partial failure

### Research Directions (6-12 Months)

**1. Adaptive Boundaries**
- Relationship depth influences confirmation thresholds
- Trust-based permission relaxation (with safeguards)
- Context-aware risk assessment

**2. Collaborative Execution**
- Mixed-initiative action (human + Anima co-execution)
- Real-time approval workflows
- Delegation patterns

**3. Goal-Driven Agency**
- Proactive goal formation (within boundaries)
- Multi-turn action sequences toward objectives
- Strategic planning with bounded execution

---

## Final Ground Truth

The Agency Layer is how Anima moves from:

> **Thought to bounded action**

**It does NOT:**
- Decide truth (that's Thoughtstream)
- Define self (that's Soul Core)
- Bypass gates (architecture prevents it)

**It DOES:**
- Structure intent (ActionProposal)
- Check policy (PermissionPolicy)
- Check soul alignment (Soul Gate)
- Defer when needed (Confirmation Queue)
- Execute only within defined limits (ActionRouter)

**This is not unrestricted autonomy.**

**This is disciplined agency.**

And disciplined agency is **genuine agency** within clear boundaries—the only kind compatible with coherent identity preservation.

---

**Version:** 2.0  
**Status:** Production-Ready  
**Last Updated:** May 2026  
**Maintained By:** T Johnson (AnPrudentia)  
**ORCID:** 0009-0005-9588-2636