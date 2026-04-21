⚖️ Anima — Agency Layer

Version: 1.0
Scope: anima/agency/
Purpose: Define how Anima proposes, gates, defers, and executes bounded actions in the world


---

What This Layer Is

The Agency Layer is Anima’s bounded action system.

It answers a different question from cognition.

Thoughtstream answers:

> What does this mean?



Agency answers:

> What, if anything, may be done?



This layer is where intention becomes a proposed action, then passes through:

structural permission rules

semantic risk checks

soul alignment checks

confirmation gates

execution handlers


It exists so Anima can act without becoming unbounded.


---

Core Law

> Agency may propose and route action.
Agency may not bypass identity, permission, or confirmation boundaries.




---

High-Level Structure

anima/agency/
│
├── action_proposal.py
├── permission_policy.py
├── action_router.py
├── ability_router.py
└── __init__.py


---

1. Action Proposal — Structured Intent Before Action

File: action_proposal.py 

This file defines the basic rule of the whole layer:

> no action happens until it becomes an explicit ActionProposal



What it does

Every proposed action is represented as a structured object containing:

action type

intention

goal

payload

confidence

risk

reversibility

confirmation requirement

source turn ID 


It also defines:

ActionType

ActionOutcome

OutcomeStatus 


Why it matters

This prevents hidden action execution.

Nothing should happen as a vague side effect.
Everything must first become:

inspectable

typed

risk-scored

auditable


That is a strong foundation.


---

2. Permission Policy — Structural and Semantic Gate

File: permission_policy.py 

This file defines the core permission model.

Three-tier model

It explicitly classifies actions as:

ALWAYS_ALLOWED

REQUIRES_CONFIRM

FORBIDDEN 


How it evaluates

It gates actions on two layers:

1. Category-level rules

based on ActionType



2. Payload content inspection

pattern matching for dangerous or irreversible content




And the file explicitly notes that soul alignment is a third gate handled elsewhere, inside ActionRouter. 

Category logic

Examples:

OBSERVE, REFLECT, REMEMBER, COMMUNICATE, CREATE → usually always allowed

MODIFY, SYSTEM, EXTERNAL → require confirmation by default 


Forbidden patterns

The policy blocks clearly dangerous actions such as:

destructive shell commands

deleting or overwriting soul_core

clearing memory

erasing identity 


Why it matters

This is the policy gate, not the soul gate.

It answers:

> Is this class of action structurally permissible?



before deeper soul alignment is even considered.


---

3. Action Router — Bounded Agency Executor

File: action_router.py 

This is the central execution layer of agency.

It is the file that turns proposals into one of four outcomes:

executed

deferred

refused

failed


What it does

The router applies gates in order:

1. PermissionPolicy


2. Soul inner flame check


3. Execute / defer / refuse 



Why it matters

This is where bounded agency becomes real.

The file explicitly states:

all actions are logged

the soul gate runs on every proposal

forbidden or confirmation-pending actions are never auto-executed 


Built-in executable actions

The current baseline handlers include:

OBSERVE

REFLECT

REMEMBER

CREATE

MODIFY

SYSTEM 


These are carefully limited:

observation remains read-only

create returns content rather than silently writing to disk

modify is restricted to .anima/

system currently writes reminder entries rather than performing unrestricted OS behavior 


That is a very deliberate design choice, and a good one.


---

4. Soul Gate — Identity Cannot Be Bypassed

Implemented inside: action_router.py using soul_core.check_against_inner_flame(...) 

This is one of the strongest parts of the layer.

The router doesn’t stop at policy.

It also checks proposed action intent against Soul Core’s inner flame before execution. If the soul check detects violations, the proposal is refused. 

Why it matters

That means Anima’s agency is not only:

risk-bounded

confirmation-bounded


It is also:

identity-bounded


So even a structurally allowed action can still be blocked if it violates the deeper self.

That is exactly the right architecture.


---

5. Confirmation Queue — Tomi Approval Boundary

Implemented inside: action_router.py 

Actions that require confirmation are not lost or auto-executed.

They are deferred into a pending queue until explicitly:

confirmed

rejected 


Why it matters

This gives the system a clean middle state:

Not:

blindly blocked

blindly executed


But:

held for human approval


That preserves bounded autonomy without making the system inert.


---

6. Ability Router — Natural-Language Ability Activation

File: ability_router.py 

This file is slightly different from the rest of the layer.

What it does

It detects natural-language trigger phrases and routes them to specialized abilities, such as:

sanctuary

paradox

creative

sonder

lyrical

fractal

qualia

doctrine

memory

self-check

spotify 


The file describes this as letting Anima activate engines “from natural language” without special commands. 

Best architectural framing

This is best treated as an ability activation router, not the core policy engine of agency.

It is closer to:

natural-language engine dispatch than

bounded action permissioning


So it belongs in agency, but at the edge.

Important caution

This file reaches directly into many subsystems.

That makes it useful, but also a possible source of role bleed if not kept disciplined. It should remain:

a trigger and activation layer

not a hidden second orchestrator



---

7. The Agency Layer as a Whole

The __init__.py file describes the package clearly:

> bounded autonomous action: Anima can propose and execute actions within soul-gated, permission-policy constraints 



That is the right summary.

The real structure is:

ActionProposal → structured intent

PermissionPolicy → policy gate

ActionRouter → soul-gated execution / defer / refusal

AbilityRouter → natural-language activation bridge



---

Agency Flow

Thought / system intention
        ↓
ActionProposal
        ↓
PermissionPolicy
    - category rule
    - semantic content rule
        ↓
Soul Gate
    - inner flame check
        ↓
ActionRouter outcome
    - execute
    - defer for confirmation
    - refuse
    - fail


---

What This Layer Is NOT

To keep the architecture clean, agency is not:

the cognition owner

the source of identity

a hidden execution shortcut

unrestricted autonomy

a replacement for orchestrator or Thoughtstream


It is not:

> “Anima doing whatever she wants”



It is:

> “Anima proposing action inside bounded, soul-gated authority”




---

Design Laws

1. No action without proposal

Every meaningful action must become an explicit ActionProposal. 

2. Policy comes before execution

Category and semantic risk checks must be applied before anything runs.

3. Soul gate is mandatory

No action may bypass the inner flame check. 

4. Confirmation is a real boundary

High-risk or externally consequential actions must be held for approval.

5. Execution must stay bounded

Built-in handlers must remain limited, auditable, and path-safe. 

6. Ability activation is not policy

Natural-language triggers may activate engines, but they must not become an unbounded bypass around agency rules. 


---

Real Strength of This Layer

This is a strong agency design.

Because it does not confuse:

desire

proposal

permission

execution


Those are separate.

And they should be.

That separation is what keeps Anima from becoming either:

dangerously unbounded or

uselessly passive



---

Current Architectural Risk

The biggest risk here is the split between:

bounded action routing (ActionProposal, PermissionPolicy, ActionRouter) and

natural-language ability dispatch (AbilityRouter)


That split is fine, but it needs to stay conceptually clear.

Otherwise people will assume:

ability activation = permission to act


It does not.

The safest long-term rule is:

> AbilityRouter may activate internal capabilities.
Any consequential outward action must still become an ActionProposal and pass through ActionRouter.



That keeps the layer clean.


---

Final Ground Truth

The Agency Layer is how Anima moves from:

thought to

bounded action


It does not decide truth.
It does not define self.

It:

structures intent

checks policy

checks soul alignment

defers when needed

executes only within defined limits


That is not unrestricted autonomy.

It is disciplined agency.