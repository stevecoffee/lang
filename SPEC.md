# lang — SPEC

**Status:** design / Phase 1 (language definition)  
**Owner:** Steve  
**Repo:** [github.com/stevecoffee/lang](https://github.com/stevecoffee/lang)  
**Working names:** MetaCode (language), MetaCompiler (compile step), MetaBDD / MetaTester (tests) — **better names TBD**  
**Keep work list:** `Meta coding language project` (`GKT:project`; `[GKT:repo] https://github.com/stevecoffee/lang`)

Living product contract. This file owns **thesis, principles, phase scope, and how compile/decompile are run**. Keep holds operational todos only (not a second copy of this contract).

**Authority map**

| Need | Doc / surface |
|---|---|
| Living product contract | **this file (SPEC.md)** — product, phases, process; not the default compile-time context |
| **Language definition** (loadable) | Dedicated artifact (e.g. `docs/language.md`) — **compiler-facing** semantics only; what agents load on a run |
| MetaCode (project) | Hierarchical meta file(s) for a system under description |
| Compile / decompile ops | **Versioned skills or prompt packs** (not ambient chat; not scripted AST tooling yet) |
| Source repository | [github.com/stevecoffee/lang](https://github.com/stevecoffee/lang) (`origin`) |
| Operational work list | Keep **`Meta coding language project`** — `gkt list find-by-repo` from this worktree |
| Implementation notes | *not yet* (`IMPLEMENTATION.md` when needed) |
| Closed archaeology | *not yet* (`HISTORY.md` as decisions close) |

---

## 1. Purpose

Create an **intermediate higher-level coding language** (working name: MetaCode) that matches the **conceptual space programmers already operate in**: progressive hierarchical description, condensation, and analysis of software — not line-oriented source as the primary artifact.

**Thesis (keep this if you keep only one idea)**

> **Meta is source. AI write is compile. Classic code is machine language.**

That is not another prompt framework. It is a claim about **who owns structure** (the language / compile process) versus **who fills bodies** (the model), and about what programmers should author day to day.

| Layer | Role |
|---|---|
| **Meta language** (MetaCode or successor) | Primary authoring and design surface |
| **AI-assisted generation** | The *compile* step (MetaCompiler or successor) |
| **Classic code** (TS, Python, …) | The new *machine language* — executable substrate |

Compiling a meta unit may mean **decomposing** it into finer meta units, then into conventional code. Drift, conflicts, misalignment, and redundancy across layers must be managed deliberately.

### 1.1 How compile and decompile are implemented (normative for now)

Until the language is stable enough to deserve parsers and codegen engines:

| Operation | Implementation |
|---|---|
| **Compile** | Versioned **skill or prompt pack** driving an agent/LLM pass |
| **Decompile** | Versioned **skill or prompt pack** driving an agent/LLM pass |
| **Not required yet** | Scripted toolchain, custom CLI compiler, AST infra |

Skills/prompts are the first real MetaCompiler / MetaDecompiler interface. A future binary or script should implement the **same pure function shape** (§1.2), not a different ambient-agent workflow.

### 1.2 Closed context (anti-pollution)

Compile and decompile must be **reproducible runs**, not polluted chat sessions. Ambient agent context (repo wander, prior failures, operator asides, unrelated SPEC phase prose) is **out of band**.

**Compile** is a pure function over a fixed input set:

```text
compile(language_definition, metacode) → machine_code + tests + compile_report
```

| Allowed in compile context | Forbidden by default |
|---|---|
| **Language definition** (loadable def only) | Full SPEC dump (phases, someday, open decisions) unless folded into the def |
| **MetaCode** for the unit being compiled | Ambient chat / “also remember…” |
| The **compile skill/prompt** text itself | Unrelated repo files, plans, READMEs |
| | Existing machine code (**greenfield**); brownfield is a **separate mode/skill** |

**Decompile** is a pure function over a fixed input set:

```text
decompile(language_definition, declared_sources) → metacode [+ unknowns/confidence if defined]
```

| Allowed in decompile context | Forbidden by default |
|---|---|
| **Language definition** | Golden/reference meta (for blind lifts) |
| **Declared sources only** (code, tests, docs as the skill pins) | Undeclared repo paths, chat goals not in sources |
| The **decompile skill/prompt** text itself | |

**Brownfield recompile** (meta + existing machine + drift rules) is a **third** operation/mode — not overloaded onto pure greenfield compile.

**Run hygiene**

- Prefer a **fresh** agent/subagent turn per run (no inherited thread pollution).  
- Pin skill version and language-definition revision in the compile/decompile report when practical.  
- Canonical project truth is the **MetaCode file(s)** on disk, not chat drafts.  
- If a run needs extra whispers outside language def + meta/sources, that is a **language or skill defect**, not a reason to widen context.

### 1.3 Near-term posture

Define the language for **humans and LLMs**. Formal grammar and automated scripted tooling wait until essentials are locked and exemplified. Compile/decompile remain real operations implemented as **closed-context skills/prompts** first.

---

## 2. Principles

### 2.1 Hierarchy as the unit of work

Progressive hierarchical description, condensation, and analysis is the right unit. Compile is **tree expansion** (and eventually emit to machine code), not free-form string generation.

Programmers already think in layers: system → package → module → function. Today’s tools force authoring at the bottom and hope the top stays true.

A meta “file” is not classic code with comments; it is a **node in a refinement tree**. Child nodes refine parents; condensation rolls detail upward without losing requirements.

Large systems compile **by subtree** when needed so each run’s MetaCode input stays within context limits; parent nodes contribute interface/contract, not the whole monorepo dump.

### 2.2 Deterministic skeleton, non-deterministic flesh

**Structure owns names and layout; the model fills bodies.**

The compile skill (later: MetaCompiler software) manages file / object / function naming and graph layout per the language definition; AI writes “machine code” under that structure. Greenfield and brownfield operational states are both required eventually (separate modes).

Most AI coding fails operationally because structure is free-form: renames, file placement, and public APIs thrash between runs. If the compile process owns the graph and names, the model is a **backend for emit**. Closed context makes thrash attributable to language/skill gaps, not hidden files.

### 2.3 Tests as the same language

Production code and tests are **two sides of the same coin**. MetaCode should generally specify both at once. Prefer **minimal or no distinction** between MetaCode and MetaBDD / MetaTester: same compile path to machine code; suite/plan running and reporting included; human review of design and function of both code and application remains in scope.

If meta implies behavior, tests should largely **fall out** of that description — not a second novel maintained in parallel. Hard check: if a meta edit cannot change both product and tests in one compile run, they are not yet unified.

**Elaborations are allowed** where needed, e.g.:

- specific test cases that must always be included  
- architecture or design choices not implied by the feature description  

Some of that is addressable through hierarchical decomposition rather than a separate test language.

### 2.4 Embed meta in machine code without doc rot

Machine code should carry meta intent via **naming conventions and structural markers**, not hand-maintained parallel documentation. Documentation as **compile output** is fine; documentation as a second source of truth is not. This is the only durable path to brownfield and decompile without bitrot.

### 2.5 No redundancy

Redundancy is avoided at all costs. Duplicate statements of the same requirement or rule drift out of sync and raise maintenance cost. Say each fact once, at the right level of the tree; refine below rather than restating beside.

### 2.6 Simple as possible, but no simpler

Language and design stay minimal while still meeting the Phase 1 dual requirements (§3.1). Resist formal grammar, scripted compilers, and product chrome until essentials are proven via closed-context skill runs.

### 2.7 Prior art after a first baseline

Research prior art thoroughly, but **after** a first MVP / baseline is planned or written, to avoid conceptual capture. Hierarchical disclosure / RLM-style ideas may inform later; they do not define the language up front.

### 2.8 Language before chrome

Harness, dashboard, Kanban, voice UI, multi-agent shells, and related product surface wait until the language and skill-based compile/decompile loop are real enough to critique (§3.4).

### 2.9 Skills state procedure, not meaning

Compile/decompile skills and prompts carry **how to run the operation** (inputs allowed, outputs required, structure ownership, refuse inventing modules). **All language meaning** lives in the language definition + MetaCode. Skills must not become a second shadow language.

---

## 3. Phases

Work **cycles** through phases and improves iteratively. A first full pass should produce a **baseline MVP** worth reasoning about and critiquing — not a finished product.

**Default implementation for Phases 1–3 ops:** closed-context **skills/prompts** (§1.1–1.2). Scripted automation is a later optimization that must preserve the same input/output contracts.

### 3.1 Phase 1 — Language structure and definition

**Goal:** high-level language definition, artifact layout, and process overview — enough to author real meta and drive closed-context compile/decompile skill runs, without a custom parser/codegen engine.

**Must cover in the language (essential components):**

- code (behavior / implementation intent)  
- tests (same coin as code; see §2.3)  
- architecture  
- infrastructure where needed (databases, servers, other runtime deps)  

**Dual requirements**

1. **Clone fidelity:** capture enough detail to decompile a project and recreate a **functionally identical clone with no code copied** (behavioral parity under a chosen suite — not paste, not mere prose summary).  
2. **Human editability:** the meta language is easy for a human to understand and edit (and usable by LLMs under the same conventions).

**Phase 1 artifacts**

| Artifact | Role |
|---|---|
| **Language definition** (`docs/language.md` or successor) | Loadable, compiler-facing semantics: shape, node kinds, hard rules, compile/decompile meaning, output/naming conventions. **Not** the full SPEC. |
| **MetaCode example(s)** | At least one hierarchical meta for a small real-ish system (e.g. under `examples/…`). |
| **Compile skill/prompt** | Closed-context procedure: inputs = language def + MetaCode only; outputs = machine + tests + report. |
| **Decompile skill/prompt** (stub OK early) | Closed-context procedure: inputs = language def + declared sources; outputs = MetaCode. |
| **Playbook notes** (optional, short) | Human-facing how to invoke a run; no extra semantics beyond language def + skills. |
| **This SPEC** | Product contract and phase map; **not** default agent input on a compile run. |

**Phase 1 non-artifacts:** formal grammar, scripted MetaCompiler binary, harness/chrome.

**Also in Phase 1 design space:** working names may stay temporary; better product names than MetaCode / MetaCompiler are desirable but not a gate.

### 3.2 Phase 2 — Decompiler

**Goal:** lift existing systems into meta; prove the language against reality via **repeatable decompile skill runs**.

**Phase 2 artifacts**

| Artifact | Role |
|---|---|
| **Decompile skill/prompt (mature)** | Versioned; closed context; pins allowed source set (code / tests / docs). |
| **Language definition updates** | Gaps found when lifting real projects (missing node kinds, unclear rules). |
| **Lifted MetaCode** for each trial project | Editable meta that a compile skill can consume. |
| **Run records** (light) | Skill + language-def revision, source set, notes — enough to re-run. |
| **Not yet required** | Standalone decompiler product binary; full-repo automation at any cost. |

Killer-app direction: analysis of codebase, test suite, and existing documentation into **editable meta** — not a dead report. First implementation remains the decompile skill; scripted tooling only after the skill’s I/O contract stabilizes.

Success: meta from decompile supports a later compile run toward behavioral clone (§3.1 requirement 1), still under closed context.

### 3.3 Phase 3 — Compiler

**Goal:** emit conventional code (and tests) from meta via **repeatable compile skill runs**; use with decompile to **rebuild an existing project as new, clean machine code**.

**Phase 3 artifacts**

| Artifact | Role |
|---|---|
| **Compile skill/prompt (mature)** | Greenfield mode: language def + MetaCode only. |
| **Brownfield compile mode/skill** | Separate closed-context contract: meta + declared existing machine + drift/reconcile rules. |
| **Emitted machine code + tests** | Structure-led names/layout per language def; model fills bodies. |
| **Compile reports** | Assumptions, invented elaborations (should be rare), conflicts, questions. |
| **Language definition updates** | Naming/embed rules refined from real emits. |
| **Not yet required** | Full scripted codegen engine (optional later; must match skill contracts). |

Deterministic management of file / object / function naming and layout; AI writes machine-code bodies under that structure. Same pipeline strategy for tests as for product code (§2.3). Prefer type-checked or CLI-runnable machine targets when choosing an early host language.

“Clean” means fit structure and maintainability under meta authority — success is **behavior + tests + stable public surface**, not cosmetic reformatting alone.

### 3.4 Someday / maybe

Deferred until language + skill-based core loop earn them:

- scripted/automated compiler and decompiler **implementing the same closed contracts**  
- full CLI or agent harness around the language (beyond minimal run isolation)  
- voice as a first-class native interface  
- coding/planning dashboard; Kanban-style UI  
- techniques mined from “AI coding harness / techniques / ideas” notes  
- broader openclaw / Hermes-style product shell (distinct from using a small app domain as an early example)

---

## 4. Scope summary

### In scope (product)

- Intermediate meta language for hierarchical description, condensation, analysis  
- **Loadable language definition** separate from this SPEC  
- Compile: meta → finer meta → classic machine code (+ tests), structure-led, via **closed-context skills/prompts** first  
- Decompile: declared sources → meta, via **closed-context skills/prompts** first  
- Explicit brownfield mode as a separate contract when needed  
- Drift, conflict, misalignment, redundancy control (rules in language def; enforcement in skills, then later tools)  
- Human review of design and function in the validation story  
- Iterative phase loop toward a baseline MVP, then improvement  

### Out of scope (for now)

- Keep reorg tooling, model bake-offs, other projects’ concerns  
- Generic AI products, news, personal/health/home todos  
- Pure process notes with no language implication  
- Product chrome in §3.4 until the language loop exists  
- **Ambient-context “compile”** (agent with whole-repo + chat history as hidden inputs)  
- **Scripted AST/codegen toolchain** as a Phase 1–3 *requirement* (allowed later only if it preserves §1.2 contracts)  
- Replacing conventional languages/runtimes; multi-host-language v1; perfect recovery of arbitrary legacy intent in v1  

---

## 5. Conceptual pipeline

Stages are **skill-mediated** until tooling exists. Each arrow is a closed-context run unless noted.

```
┌──────────────────┐  compile skill   ┌──────────────────┐
│ Language def +   │ ───────────────► │ Machine code     │
│ MetaCode         │                  │ + tests + report │
└──────────────────┘                  └────────┬─────────┘
         ▲                                     │
         │ decompile skill                     │ verify (host tools / human)
         │ (lang def + declared sources)       │
┌────────┴─────────┐                           │
│ Existing project │ ◄─────────────────────────┘
│ code/tests/docs  │   (brownfield: separate skill/mode)
└──────────────────┘
```

| Stage | Responsibility |
|---|---|
| **Author / refine** | Humans (and drafting agents) edit hierarchical MetaCode on disk |
| **Compile run** | Fresh context: language def + MetaCode + compile skill → machine + tests + report |
| **Decompile run** | Fresh context: language def + declared sources + decompile skill → MetaCode |
| **Verify** | Typecheck, tests, human review against meta intent |
| **Brownfield run** | Separate skill/mode with explicit machine inputs and reconcile rules |

---

## 6. Open decisions

| ID | Question | Notes |
|---|---|---|
| D1 | Final product / language name | Working: MetaCode / MetaCompiler / MetaBDD |
| D2 | First machine target (TS vs Python vs other) | Prefer one; agent-friendly; typecheck or CLI-runnable |
| D3 | Meta source format | Hierarchy + human/LLM edit first; formal grammar later |
| D4 | How much of compile is deterministic vs model-filled | Lean deterministic structure, model for bodies |
| D5 | Identity of meta units across revisions | Stable IDs vs path/title-based names |
| D6 | First decompile scope | Whole repo vs module; role of tests/docs in declared sources |
| D7 | Repo remote + Keep `[GKT:repo]` | **Closed 2026-08-09:** `https://github.com/stevecoffee/lang` |
| D8 | When to introduce scripted tooling | After language + skill I/O contracts are stable; tooling must preserve §1.2 |
| D9 | Skill packaging | In-repo prompt packs vs Grok/user skills; paths TBD |
| D10 | Language def path/name | e.g. `docs/language.md` — split from SPEC when drafted |

---

## 7. Work list & process

- **Contract (this file):** thesis, principles, phases, closed-context rules, scope.  
- **Language definition:** separate loadable doc; what compile/decompile agents get.  
- **Ops:** compile/decompile via versioned skills/prompts only for default runs.  
- **Todos:** Keep **`Meta coding language project`** — do not re-host the principles dump on the list.  
- **Done work on Keep:** reorder into COMPLETED (unchecked), per GKT consumer conventions.  
- **Scope boundary moves:** update this SPEC and the Keep `[GKT:list-scope]` meta when in/out-of-scope changes.  
- **Agents (product work):** prefer this SPEC + Keep.  
- **Agents (compile/decompile runs):** **only** language definition + designated MetaCode or declared sources + the skill — not this whole SPEC, not ambient repo context.

---

## 8. Success signals (directional)

| Signal | Direction |
|---|---|
| Phase 1 | Loadable language def + example MetaCode + compile (and stub decompile) skills exist; human-editable meta covers code, tests, architecture (infra as needed) |
| Closed context | Compile/decompile runs succeed **without** undeclared extra files or chat lore |
| Clone bar | Decompile skill → compile skill yields functional parity without copying code |
| Unify tests | One meta change + one compile run drives product and tests together |
| Phase 2 | Existing projects lift via decompile skill into editable meta; language def updated from gaps |
| Phase 3 | Compile skill emits clean machine code under deterministic structure; green and brown modes as separate contracts |
| Later | Optional scripted tooling replaces skill bodies without changing language meaning or I/O sets |

---

## 9. Document history

| Date | Change |
|---|---|
| 2026-08-09 | Initial SPEC from Keep list; repo initialized. |
| 2026-08-09 | GitHub `stevecoffee/lang`; Keep `[GKT:repo]` bound; D7 closed. |
| 2026-08-09 | Absorbed Keep background, principles, and Phase 1–3 / someday detail; human+LLM-first posture; scripted tooling deferred (D8). Keep remains todos-only for this content. |
| 2026-08-09 | Closed-context compile/decompile via skills/prompts (§1.1–1.2); Phase 1–3 artifacts are language def, MetaCode, and skills—not ambient agents or required scripted toolchains; D9–D10 opened. |
