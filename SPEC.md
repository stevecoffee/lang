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
| **Language definition** (loadable) | [`docs/language.md`](docs/language.md) — **compiler-facing** semantics only; what agents load on a run |
| MetaCode (example) | e.g. [`examples/todo/meta.md`](examples/todo/meta.md) — hierarchical meta for a system |
| Compile / decompile ops | [`skills/metacompile`](skills/metacompile/SKILL.md), [`skills/metadecompile`](skills/metadecompile/SKILL.md); playbooks under [`docs/playbooks/`](docs/playbooks/) |
| Source repository | [github.com/stevecoffee/lang](https://github.com/stevecoffee/lang) (`origin`) |
| Operational work list | Keep **`Meta coding language project`** — `gkt list find-by-repo` from this worktree |
| Repo map | [`README.md`](README.md) |
| Implementation notes | *not yet* (`IMPLEMENTATION.md` when needed) |
| Closed archaeology | *not yet* (`HISTORY.md` as decisions close) |

---

## 1. Purpose

Create an **intermediate higher-level language** (working name: MetaCode) for describing software as people actually think about it: progressive **hierarchical** description, condensation, and analysis — not line-oriented source as the primary artifact.

**Accessible to non-programmers.** Meta states product intent, behavior, and experience in plain language. **Implementation detail** (modules, frameworks, file layout, algorithms) is chosen at **compile** time by the LLM (later: tools), not required in meta.

**Thesis (keep this if you keep only one idea)**

> **Meta is source. AI write is compile. Classic code is machine language.**

That is not another prompt framework. It is a claim about **who owns product truth** (meta) versus **who fills implementation** (compile / model).

| Layer | Role |
|---|---|
| **Meta language** (MetaCode or successor) | Primary authoring surface — hierarchical, plain language |
| **AI-assisted generation** | The *compile* step — implementation + classic code (+ tests) |
| **Classic code** (TS, Python, …) | The new *machine language* — executable substrate |

**Hierarchy is real:** many nodes (eventually many files), not one giant meta blob. Early on, **sections may stand in for child nodes**. **Format later** — content and hierarchy first.

Compiling a unit may mean refining into child meta, then into conventional code. Drift and redundancy are managed deliberately.

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

Define the language for **humans (including non-programmers) and LLMs**. Formal grammar/formatting and automated scripted tooling wait until content and hierarchy are solid. Compile/decompile are closed-context skills/prompts first; compile is expected to supply implementation detail.

---

## 2. Principles

### 2.1 Hierarchy as the unit of work

Progressive hierarchical description, condensation, and analysis is the right unit. Compile is **tree expansion** (and eventually emit to machine code), not free-form string generation.

**Not one giant file.** The system is a **tree of meta nodes**. Root = whole product in one breath; children = one concern each. Same idea as small source files. Until multi-file meta is worth the friction, **sections in one file stand in for child nodes** — then split when a section outgrows working memory.

A meta node is not classic code with comments; it is a unit of human understanding. Child nodes refine parents; condensation rolls detail upward without losing requirements.

**Working-memory budget:** each node stays small (about one screen). Detail goes **down**, not into a longer essay. Normative detail: [`docs/language.md`](docs/language.md).

Compile **by subtree** when needed; parents give context, not the entire tree dumped into every run.

### 2.2 Product in meta; implementation at compile

**Meta owns product truth. Compile owns implementation fill.**

Authors (including non-programmers) state what it is, what you can do, and rules that matter to users. They do **not** have to specify modules, frameworks, or file trees.

Where meta **does** pin a user-facing structure or rule, compile honors it. Where meta is silent on engineering structure, the LLM chooses simply and reports choices. Greenfield and brownfield modes both required eventually (separate).

Closed context makes bad inventing of *product* scope visible; inventing *implementation* under clear product meta is expected.

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

| Artifact | Role / path |
|---|---|
| **Language definition** | [`docs/language.md`](docs/language.md) — loadable semantics: shape, hard rules, compile/decompile meaning. **Not** the full SPEC. |
| **MetaCode example(s)** | First example: [`examples/todo/meta.md`](examples/todo/meta.md) (full-screen todo editor). Emit dir: `examples/todo/machine/`. |
| **Compile skill** | [`skills/metacompile/SKILL.md`](skills/metacompile/SKILL.md) — inputs = language def + MetaCode only. |
| **Decompile skill** | [`skills/metadecompile/SKILL.md`](skills/metadecompile/SKILL.md) — inputs = language def + declared sources. |
| **Playbooks** | [`docs/playbooks/compile.md`](docs/playbooks/compile.md), [`docs/playbooks/decompile.md`](docs/playbooks/decompile.md) — invoke runs; no extra language meaning. |
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
| D9 | Skill packaging | **In-repo** under `skills/metacompile` and `skills/metadecompile`; may symlink/copy into agent skill dirs later |
| D10 | Language def path/name | **Closed 2026-08-09:** `docs/language.md` |

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
| 2026-08-09 | Scaffold: `docs/language.md`, playbooks, `skills/metacompile|metadecompile`, `examples/todo` (full-screen todo editor meta); D10 closed; D9 in-repo skills. |
| 2026-08-09 | Critique pass: thin `examples/todo/meta.md`; language §2.1 working-memory budget / progressive disclosure; SPEC §2.1 notes concept limit per file. |
| 2026-08-09 | Non-programmer authors; LLM fills implementation; hierarchy as multi-node tree (sections as stand-in); format deferred; language v0.3. |
