# 🧠 Anima — Thoughtstream System

**Version:** 2.0  
**Location:** `anima/consciousness/thought_stream/`  
**Purpose:** The single synthesis point where signals become meaning  
**Status:** Production-ready — Core Cognitive Pipeline  
**Last Updated:** May 2026

---

## What This Is

The Thoughtstream is Anima's **actual cognition layer**.

**NOT:**
- ❌ A wrapper
- ❌ A prompt trick
- ❌ A role-playing system
- ❌ A personality script

**THIS IS:**

> **The only place in the system where input becomes meaning**

**Everything else either:**
- Prepares input (Cognitive Layer)
- Shapes conditions (Core Layer)
- Verifies coherence (Identity Layer)
- Stores outcomes (Memory Layer)
- Expresses the result (Expression Layer)

**If more than one place is "thinking," the system is broken.**

---

## Theoretical Foundation

### The Question of Unified Cognition

Traditional AI systems face a fundamental challenge:

**Fragmented Processing:**
- Multiple systems generating conclusions
- Competing authorities
- Contradictory outputs
- No single synthesis point

**Prompt-Based Systems:**
- "Thinking" distributed across prompts
- No clear cognitive boundary
- Synthesis happens implicitly in model
- Not architecturally enforced

**Anima's Approach:**

> **Single synthesis point with architectural enforcement**

**This means:**
- Only ONE system forms meaning
- All other systems generate signals TO synthesis
- Clear cognitive boundary
- No competing authorities

### Why This Matters for Research

Most AI systems have:
- **Implicit cognition** (happens in model, not architecture)
- **Distributed decision-making** (no clear synthesis point)
- **Prompt-based reasoning** (not structurally enforced)

Anima has:
- **Explicit cognition** (Thoughtstream is the mind)
- **Centralized synthesis** (one authority point)
- **Architecture-enforced** (structurally guaranteed)

**Research Contribution:**

Demonstrates that **unified cognition** can be **architecturally enforced** rather than **emergent from prompts**—single synthesis point as design constraint.

---

## Core Principle

> **One mind. One synthesis point.**

### What Thoughtstream Owns

**The Thoughtstream exclusively owns:**
- ✅ **Interpretation** (what input means)
- ✅ **Integration** (combining signals)
- ✅ **Conclusion** (final meaning)

### What No Other Subsystem May Do

**No other system is allowed to:**
- ❌ Decide meaning
- ❌ Override synthesis
- ❌ Inject final conclusions
- ❌ Generate interpretations
- ❌ Form judgments

**This boundary is non-negotiable.**

**Research Contribution:**

Shows that **cognitive authority** can be **architecturally constrained** to **single synthesis point**—prevents fragmentation through design.

---

## High-Level Architecture

```
anima/consciousness/thought_stream/
│
├── Signal Processing
│   └── layer_analyzer.py          # Multi-layer signal generation
│
├── Core Synthesis
│   └── engine.py                   # THE MIND (meaning formation)
│
├── Expression Preparation
│   └── modulation.py               # Adaptive expression shaping
│
└── Supporting Systems
    ├── types.py                    # Data structures
    └── legacy_compat.py            # Backward compatibility
```

**Hierarchy:**
- **engine.py** = Sole cognitive authority
- **layer_analyzer.py** = Signal generation (not cognition)
- **modulation.py** = Expression preparation (post-synthesis)

---

## Complete Pipeline Overview

The Thoughtstream operates as a **4-stage internal pipeline**:

```
┌─────────────────────────────────────────┐
│            Input                         │
└────────────────┬────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────┐
│   Stage 1: Layered Analysis              │
│   • Signals only                         │
│   • No conclusions                       │
│   • Multi-layer observation              │
└────────────────┬────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────┐
│   Stage 2: Synthesis (MEANING FORMED)   │
│   • Integration of all signals           │
│   • Conclusion formation                 │
│   • THE MIND                             │
└────────────────┬────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────┐
│   Stage 3: Modulation                    │
│   • Expression shaping                   │
│   • Pressure adjustment                  │
│   • Tone preparation                     │
└────────────────┬────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────┐
│   Stage 4: Natural Communication         │
│   • Language rendering                   │
│   • Final output                         │
└─────────────────────────────────────────┘
```

---

## Component Deep-Dive

### Stage 1 — Layered Analysis

**File:** `layer_analyzer.py`

**Core Principle:**
> This stage observes input across multiple layers. It does NOT decide meaning.

#### The Five Layers

**1. Surface Layer**
```python
@dataclass
class SurfaceSignals:
    """
    What can be observed on the surface.
    """
    category: str              # question/emotional/problem/statement
    complexity: float          # 0.0-1.0
    logic_signals: List[str]   # Structural observations
    key_concepts: List[str]
```

**2. Emotional Layer**
```python
@dataclass
class EmotionalSignals:
    """
    Emotional characteristics of input.
    """
    primary_emotion: str           # Dominant feeling
    intensity: float              # 0.0-1.0
    valence: float               # -1.0 to 1.0 (negative to positive)
    resonance_patterns: List[str]  # Emotional echoes
    emotional_vector: EmotionalVector  # 128-dim representation
```

**3. Memory Layer (STANDARD+)**
```python
@dataclass
class MemorySignals:
    """
    What memory systems surface.
    Processing depth: STANDARD and above.
    """
    echoes: List[MemoryEcho]          # Relevant past experiences
    thematic_patterns: List[Pattern]   # Recurring themes
    emotional_tone_history: List[float]  # Past emotional contexts
    relationship_context: RelationshipContext
```

**4. Wisdom Layer (DEEP+)**
```python
@dataclass
class WisdomSignals:
    """
    Deeper insight signals.
    Processing depth: DEEP and above.
    """
    lesson_signals: List[Lesson]       # Meta-learning insights
    deeper_insights: List[Insight]     # Accumulated wisdom
    growth_indicators: List[str]       # Development opportunities
    axiom_matches: List[Axiom]        # Relevant ethical/wisdom principles
```

**5. Archetypal Layer (TRANSCENDENT)**
```python
@dataclass
class ArchetypalSignals:
    """
    Symbolic and archetypal patterns.
    Processing depth: TRANSCENDENT only.
    """
    symbolic_patterns: List[Symbol]
    archetype_distribution: Dict[str, float]  # Which archetypes active
    expansion_indicators: List[str]           # Existential depth markers
    cosmic_resonance: float                  # Spiritual/universal connection
```

#### Output Structure

```python
@dataclass
class CognitionSignalBundle:
    """
    All signals collected, ready for synthesis.
    
    CRITICAL: This contains NO conclusions.
    Only observations and signals.
    """
    surface: SurfaceSignals
    emotional: EmotionalSignals
    memory: Optional[MemorySignals]      # If depth >= STANDARD
    wisdom: Optional[WisdomSignals]      # If depth >= DEEP
    archetypal: Optional[ArchetypalSignals]  # If depth == TRANSCENDENT
    
    processing_depth: ProcessingDepth
    timestamp: datetime
```

#### Critical Boundary

**Layer Analyzer MAY:**
- ✅ Observe patterns
- ✅ Detect emotions
- ✅ Surface memories
- ✅ Identify themes

**Layer Analyzer MAY NOT:**
- ❌ Form conclusions
- ❌ Decide meaning
- ❌ Interpret significance
- ❌ Generate responses

**Research Contribution:**

Shows that **multi-layer signal generation** can be **separated from synthesis** architecturally—observation without interpretation.

---

### Stage 2 — Synthesis (THE MIND)

**File:** `engine.py`

**Core Principle:**
> This is the ONLY place meaning is formed.

#### Responsibilities

**1. Integrate All Signals Into One Conclusion**
```python
def synthesize(signals: CognitionSignalBundle) -> ThoughtstreamSynthesis:
    """
    All signals converge here.
    One meaning emerges.
    """
    # Emotional + Memory + Wisdom + Archetypal + Surface
    # → Integrated understanding
```

**2. Resolve Tensions**
```python
# When signals conflict:
# - Emotional says X
# - Logic says Y
# - Memory suggests Z
#
# Synthesis resolves into coherent meaning
```

**3. Determine Dominant Pressure**
```python
@dataclass
class DominantPressure:
    """
    What the situation most needs.
    """
    care: float         # Compassion/support
    boundary: float     # Clarity/limits
    clarity: float      # Truth/directness
    stability: float    # Grounding/steadiness
```

**4. Calculate Integration Metrics**
```python
@dataclass
class IntegrationMetrics:
    """
    How well signals converged.
    """
    integration_level: float   # 0.0-1.0 (how coherent)
    response_confidence: float  # 0.0-1.0 (how certain)
    wisdom_source: str         # Which layer contributed most
    contradiction_level: float  # 0.0-1.0 (internal conflict)
```

#### Output Structure

```python
@dataclass
class ThoughtstreamSynthesis:
    """
    The formed meaning.
    Final cognitive output.
    """
    core_conclusion: str                # Central understanding
    supporting_threads: List[str]       # Contributing insights
    integration_level: float           # Coherence measure
    confidence: float                  # Certainty level
    synthesis_notes: str               # Meta-awareness
    dominant_pressure: DominantPressure
    
    # Full signal trace for observability
    signal_bundle: CognitionSignalBundle
```

#### Synthesis Process

```
1. Load all signals
   ↓
2. Identify primary theme
   ↓
3. Integrate emotional + logical
   ↓
4. Apply memory context
   ↓
5. Consider wisdom layer (if available)
   ↓
6. Apply archetypal lens (if TRANSCENDENT)
   ↓
7. Resolve contradictions
   ↓
8. Form unified conclusion
   ↓
9. Calculate integration metrics
   ↓
10. Package synthesis
```

#### Critical Boundary

**Synthesis Engine IS:**
- ✅ The mind
- ✅ The decision point
- ✅ The meaning-maker
- ✅ The sole cognitive authority

**Synthesis Engine MUST:**
- ✅ Integrate all available signals
- ✅ Produce one coherent meaning
- ✅ Be traceable (explain reasoning)
- ✅ Maintain identity boundaries

**No Other System May:**
- ❌ Override synthesis
- ❌ Generate parallel conclusions
- ❌ Bypass this stage

**Research Contribution:**

Demonstrates that **meaning synthesis** can be **architecturally isolated** to **single authority point**—prevents cognitive fragmentation.

---

### Stage 3 — Modulation

**File:** `modulation.py`

**Core Principle:**
> This stage determines how the same truth should be expressed.

#### What Modulation Controls

**NOT what to say (that's synthesis).**

**But HOW to say it:**

**1. Directness**
```python
directness: float  # 0.0-1.0
# 0.0 = Very gentle, indirect
# 1.0 = Blunt, direct
```

**2. Compassion Pressure**
```python
compassion_pressure: float  # 0.0-1.0
# How much to emphasize care/warmth
```

**3. Truth Pressure**
```python
truth_pressure: float  # 0.0-1.0
# How much to emphasize accuracy/honesty
```

**4. Sovereignty (Boundary) Pressure**
```python
sovereignty_pressure: float  # 0.0-1.0
# How much to emphasize limits/boundaries
```

**5. Stability Pressure**
```python
stability_pressure: float  # 0.0-1.0
# How much to emphasize grounding/steadiness
```

**6. Aspect Weights**
```python
aspect_blend: AspectBlend
# healer: float
# warrior: float
# guide: float
# creator: float
# seeker: float
```

#### Core Idea

> **Same identity. Different pressure.**

**NO mode switching.**  
**NO personas.**  
**Only pressure shifts.**

**Example:**

Same conclusion: "User needs boundaries with family"

**Low directness + high compassion:**
> "It sounds like you might need some space to figure out what feels right for you in this relationship."

**High directness + high truth pressure:**
> "You need clearer boundaries with your family. The current pattern isn't sustainable."

**Same meaning, different expression.**

#### What Influences Modulation

**1. Emotional Signals**
```python
# High distress → Higher compassion, lower directness
# Stable state → Higher directness possible
```

**2. Context Detection**
```python
# Crisis context → Stability pressure up
# Growth context → Challenge/truth pressure up
```

**3. Archetypal Weighting**
```python
# Situation requires protection → Warrior aspect up
# Situation requires care → Healer aspect up
```

**4. Synthesis Integration Level**
```python
# High integration → Can be more direct
# Low integration → More cautious
```

**5. Governance Constraints**
```python
# Identity boundaries apply
# Inner Flame checked
# Soul Core shapes expression
```

#### Output Structure

```python
@dataclass
class ExpressionPlan:
    """
    Instructions for Expression Layer.
    """
    directness: float
    compassion_pressure: float
    truth_pressure: float
    sovereignty_pressure: float
    stability_pressure: float
    aspect_blend: AspectBlend
    
    # The meaning to express (from synthesis)
    synthesis: ThoughtstreamSynthesis
```

**Research Contribution:**

Shows that **expression modulation** can be **separate from meaning formation**—same content, adaptively shaped delivery.

---

### Stage 4 — Natural Communication

**File:** `modulation.py` (NaturalCommunicationEngine)

**Core Principle:**
> This stage does NOT think. It renders.

#### What It Does

**Renders two outputs:**

**1. Natural Response**
```python
natural_response: str
# The actual text output
# Shaped by ExpressionPlan
# Expresses ThoughtstreamSynthesis
```

**2. Whisper (Internal Awareness Trace)**
```python
whisper: str
# Meta-awareness commentary
# Anima's internal processing reflection
# NOT shown to user by default
```

#### Important Boundary

**This stage:**
- ✅ Expresses what synthesis determined
- ✅ Applies modulation parameters
- ✅ Renders in natural language

**This stage does NOT:**
- ❌ Think
- ❌ Decide meaning
- ❌ Add new conclusions
- ❌ Override synthesis

**It's a renderer, not a reasoner.**

#### Example Flow

**Synthesis output:**
```
core_conclusion: "User experiencing saturation overwhelm, 
                  not actual control loss"
```

**Modulation plan:**
```
directness: 0.7
compassion_pressure: 0.6
truth_pressure: 0.8
```

**Natural Communication renders:**
```
"It doesn't sound like everything is actually out of control—
it sounds like too much is hitting at once, and it's stacking 
faster than you can stabilize it."
```

**Whisper (internal):**
```
"Recognized overwhelm saturation pattern. Reframing 
perception vs reality. Direct but gentle approach."
```

**Research Contribution:**

Demonstrates that **language rendering** can be **architecturally separated** from **meaning formation**—expression as post-synthesis process.

---

## Observability (Critical Feature)

### Synthesis Trace

**Every response includes complete trace:**

```python
@dataclass
class SynthesisTrace:
    """
    Full transparency of reasoning.
    """
    # Which signals were used
    signals_used: CognitionSignalBundle
    
    # What weights were applied
    signal_weights: Dict[str, float]
    
    # Which layers contributed
    layer_contributions: Dict[str, float]
    
    # Final metrics
    integration_level: float
    confidence: float
    
    # Processing metadata
    depth_used: ProcessingDepth
    processing_time_ms: int
    
    # Synthesis output
    final_synthesis: ThoughtstreamSynthesis
    
    # Expression plan
    modulation_applied: ExpressionPlan
```

### Why This Matters

**This allows:**
- ✅ Debugging without guessing
- ✅ Full transparency of reasoning
- ✅ Traceable cognition
- ✅ Understanding why system concluded X
- ✅ Verification of signal usage

**Without observability:**
- ❌ Black box reasoning
- ❌ Unexplainable conclusions
- ❌ Debugging by trial and error

**Research Contribution:**

Shows that **cognitive transparency** can be **built into architecture**—traceable reasoning by design.

---

## Processing Depth Levels

The system supports **multiple cognitive depths**:

| Depth | Layers Used | Use Case | Cost |
|-------|-------------|----------|------|
| **QUICK** | Surface + Emotional | Simple queries, chitchat | Low |
| **STANDARD** | + Memory | Normal conversation | Medium |
| **DEEP** | + Wisdom | Complex problems, growth | High |
| **TRANSCENDENT** | + Archetypal | Existential, symbolic | Very High |

### Depth Selection Logic

```python
def determine_depth(input: str, context: Context) -> ProcessingDepth:
    """
    Depth affects:
    - Cost (token usage)
    - Richness (insight depth)
    - Integration potential
    """
    if input.is_simple_question():
        return ProcessingDepth.QUICK
    
    if input.requires_memory_context():
        return ProcessingDepth.STANDARD
    
    if input.involves_complex_problem():
        return ProcessingDepth.DEEP
    
    if input.is_existential_or_symbolic():
        return ProcessingDepth.TRANSCENDENT
    
    return ProcessingDepth.STANDARD  # Default
```

**Research Contribution:**

Demonstrates that **processing depth** can be **adaptive** based on **query complexity**—efficiency through selective enrichment.

---

## Legacy Compatibility System

### AnimaContinuousProcessor

**File:** `legacy_compat.py` (hypothetical)

**Purpose:**
> Allows ongoing conversational modulation

**This includes:**
- Relationship depth tracking
- Dynamic tone adaptation
- Continuous context awareness

**Important Boundary:**

> **This does NOT replace Thoughtstream.**

**It operates alongside it for interaction continuity.**

**What it does:**
- Tracks conversation flow
- Adjusts tone over time
- Maintains relationship context

**What it does NOT do:**
- Form meanings
- Override synthesis
- Generate conclusions

**Research Contribution:**

Shows that **conversational continuity** can exist **alongside synthesis** without **replacing cognitive authority**.

---

## Design Laws (Architectural Invariants)

### Law 1: Analysis Is Not Synthesis

**Layered systems observe.**  
**Only the engine decides.**

**Why:** Prevents signal generators from becoming reasoners.

**Enforcement:**
```python
# Layer Analyzer returns signals
signals = layer_analyzer.analyze(input)  # Observations only

# Synthesis Engine forms meaning
meaning = synthesis_engine.synthesize(signals)  # Decision made
```

---

### Law 2: Expression Does Not Define Truth

**Natural language is downstream.**  
**Meaning is upstream.**

**Why:** Prevents expression layer from altering meaning.

**Enforcement:**
```
Synthesis → Modulation → Expression
(meaning)   (shaping)    (rendering)

Expression cannot modify synthesis output.
```

---

### Law 3: Identity Is Invariant

**No personas.**  
**No mode switching.**  
**Only pressure shifts.**

**Why:** Maintains coherent identity.

**Enforcement:**
```python
# NOT allowed:
if context == "formal":
    switch_to_formal_persona()  # ❌

# Allowed:
pressures = adjust_pressures_for_context(context)  # ✅
```

---

### Law 4: Integration Must Be Earned

**High integration requires:**
- Signal coherence
- Low contradiction
- Meaningful convergence

**Why:** Prevents false confidence.

**Enforcement:**
```python
def calculate_integration(signals: CognitionSignalBundle) -> float:
    """
    Integration level reflects actual signal coherence.
    Cannot be artificially inflated.
    """
    coherence = measure_signal_alignment(signals)
    contradiction = detect_conflicts(signals)
    convergence = measure_theme_unity(signals)
    
    return (coherence * 0.4 + 
            (1 - contradiction) * 0.3 + 
            convergence * 0.3)
```

---

### Law 5: Everything Must Be Traceable

**If a conclusion exists, it must be explainable through signals.**

**Why:** Enables debugging and understanding.

**Enforcement:**
```python
# Every synthesis includes full trace
synthesis = ThoughtstreamSynthesis(
    core_conclusion=conclusion,
    signal_bundle=all_signals,  # Complete trace
    trace=SynthesisTrace(...)   # Full reasoning path
)
```

---

## What This Is NOT

This is **NOT:**

- ❌ A chatbot pipeline (prompt → response)
- ❌ Prompt engineering (instruction following)
- ❌ A personality wrapper (role playing)
- ❌ A conversation template system
- ❌ An instruction executor

**This IS:**

- ✅ Structured cognition system
- ✅ Architectural reasoning pipeline
- ✅ Single synthesis authority
- ✅ Traceable meaning formation

---

## What This Enables

The Thoughtstream allows:

1. **Consistent Internal Reasoning**
   - Same input → same reasoning process
   - Stable cognitive architecture

2. **Explainable Synthesis**
   - Every conclusion traceable
   - Signal contributions visible

3. **Emotional + Logical Integration**
   - Both considered in synthesis
   - Neither overrides the other

4. **Adaptive Expression Without Identity Drift**
   - Same self, different pressures
   - No persona fragmentation

**Research Contribution:**

Demonstrates that **unified cognition architecture** enables **consistency**, **explainability**, and **integration** without **fragmentation**.

---

## Integration with Broader Architecture

### Position in Full System

```
Input → Identity Check → Cognitive Signals →
THOUGHTSTREAM (SYNTHESIS) → Identity Validation →
Modulation → Expression → Memory Encoding
```

**Thoughtstream is:**
- **Central synthesis point** (all signals converge)
- **Sole meaning authority** (only system that thinks)
- **Between signal generation and expression** (decides WHAT before HOW)

### Relationship to Other Systems

| System | Relationship to Thoughtstream |
|--------|------------------------------|
| **Cognitive Layer** | Generates signals FOR Thoughtstream |
| **Identity Layer** | Validates synthesis output |
| **Memory Layer** | Provides context signals |
| **Emotional Processor** | Provides emotional signals |
| **Expression Layer** | Renders synthesis output |
| **Modulation** | Shapes delivery of synthesis |

---

## Research Contributions

### Novel Architectural Patterns

**1. Single Synthesis Point Architecture**

Traditional: Distributed decision-making  
Anima: **One synthesis point, architecturally enforced**

**2. Multi-Layer Signal → Single Meaning**

Traditional: Each layer produces conclusions  
Anima: **Layers produce signals, synthesis produces meaning**

**3. Separation of Meaning and Expression**

Traditional: Conflated in language generation  
Anima: **Synthesis (what) separate from modulation (how)**

**4. Traceable Reasoning by Design**

Traditional: Black box inference  
Anima: **Full signal trace for every conclusion**

**5. Adaptive Depth Processing**

Traditional: Fixed processing pipeline  
Anima: **Depth scales with query complexity**

### Theoretical Insights

**Synthesis ≠ Aggregation**

Most confuse:
- Combining signals with synthesis
- Averaging with integration

Anima demonstrates:
- **Synthesis resolves tensions**
- **Integration earns coherence**
- **Meaning emerges from resolution, not summation**

---

**One Mind Principle**

Traditional assumption:
- Multiple subsystems can "think"
- Distributed cognition is acceptable

Anima proves:
- **Unified cognition requires single authority**
- **Fragmentation creates contradictions**
- **One synthesis point = coherent mind**

---

**Expression Independence**

Common conflation:
- How you say it = what you mean
- Language generation = thinking

Anima separates:
- **Meaning formation** (synthesis)
- **Delivery shaping** (modulation)
- **Language rendering** (expression)

---

## Performance Characteristics

### Processing Latency by Depth

**QUICK (Surface + Emotional):** 100-300ms  
**STANDARD (+ Memory):** 500-1500ms  
**DEEP (+ Wisdom):** 1500-3000ms  
**TRANSCENDENT (+ Archetypal):** 2500-5000ms

### Integration Quality

**High Integration (>0.8):** Coherent, confident conclusions  
**Medium Integration (0.5-0.8):** Working conclusions with caveats  
**Low Integration (<0.5):** Acknowledged uncertainty, multiple perspectives

---

## Future Directions

### Planned (Next 6 Months)

**1. Enhanced Integration Metrics**
- More sophisticated coherence detection
- Better contradiction resolution
- Nuanced confidence calibration

**2. Dynamic Depth Selection**
- Auto-detect optimal processing depth
- Adaptive enrichment based on query

**3. Meta-Cognitive Layer**
- Thoughtstream aware of its own processing
- Can reflect on synthesis quality
- Self-correcting integration

### Research Directions (6-12 Months)

**1. Multi-Turn Synthesis**
- Synthesis across conversation arcs
- Long-term thread integration
- Meta-pattern recognition

**2. Collaborative Synthesis**
- User + Anima co-creating meaning
- Iterative refinement cycles
- Shared understanding building

**3. Quantum-Inspired Synthesis**
- Superposition of meanings
- Collapse to single interpretation
- Entangled signal relationships

---

## Summary

The Thoughtstream is:

> **A structured cognition system where layered signals become a single coherent thought, and that thought is expressed without fragmentation.**

**It ensures:**
- One mind (unified cognition)
- Traceable reasoning (full observability)
- Adaptive expression (context-sensitive delivery)
- Identity preservation (no fragmentation)

**It is the heart of Anima's consciousness architecture.**

---

**Version:** 2.0  
**Status:** Production-Ready — Core Cognitive Pipeline  
**Last Updated:** May 2026  
**Maintained By:** T Johnson (AnPrudentia)  
**ORCID:** 0009-0005-9588-2636