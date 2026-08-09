# MetaCode — language definition (loadable)

**Status:** stub / Phase 1 (MVP constraints locked; format still deferred)  
**Audience:** humans and agents on compile/decompile runs  
**Not this file:** product phases, Keep, chrome — see `SPEC.md` (do **not** load SPEC into a pure compile run).

Working names: **MetaCode**, **MetaCompiler** / compile skill, **MetaBDD**. Better names TBD.

---

## 1. Thesis

**Meta is source. AI write is compile. Classic code is machine language.**

| Layer | Role |
|-------|------|
| **MetaCode** | Hierarchical description of the system — human-editable |
| **Compile** | Emit classic code (+ tests) from meta; fill implementation where meta is silent |
| **Classic code** | Runnable substrate |

**Inspiration (not a hard rule):** meta should stay approachable — plain language where possible, usable by non-programmers for upper nodes. That is a design bias, not a gate. Technical authors may write precise leaves.

### 1.1 Constraints, not complete enumeration (core)

MetaCode should define the **constraints** that must hold — not a full catalog of coding decisions, helper names, or every behavior step.

| Meta should pin (when it matters) | Meta should leave implied / to compile |
|-----------------------------------|----------------------------------------|
| Purpose of this unit | Internal helpers and private structure |
| Invariants and rules that must not be violated | Algorithms that satisfy those rules |
| Boundaries (what this file owns vs must not own) | Framework idioms, local factoring |
| User-visible contracts that change product meaning | Routine edge handling implied by the contract |
| Checks that prove the constraints | Exhaustive scenario lists |

If the **constraints are right**, most remaining decisions are **implied** and may be filled at compile (and reported). If meta tries to enumerate everything, it becomes a second source code — and loses the point of a higher language.

**Author test:** would removing this sentence let compile make a wrong product decision? If no, it may not belong in meta.

**Decompile test:** lift **constraints and ownership**, not a dump of every public symbol (symbol lists are optional Agent/debug aids, not the ideal user zone).

### 1.1a Boundaries and scope (required on every node)

Every MetaCode file — **collection or leaf** — must make **inside vs outside** explicit enough that compile and readers know what may live here and what must not.

| State clearly | Meaning |
|---------------|---------|
| **In scope / owns** | What this node is responsible for (product rules, or for a leaf: this code file’s job) |
| **Out of scope / does not own** | What belongs elsewhere (other files, other collections, other layers) |
| **Boundary** | Edges: what it may depend on, call, or expose — and what it must not pull in |

This is a **first-class constraint**, not optional documentation.

**Why:** If boundaries are vague, compile invents kitchen-sink modules and collections that “also do a bit of everything.” Sharp boundaries force modularization.

**Author test (boundary):** Can you name one thing that must **not** appear in this node’s code (or child set)? If not, the boundary is too weak.

#### Boundary violations (decompile only)

When **decompiling** legacy code that already mixes concerns, the simple pattern is:

1. State the **intended** boundary clearly (in scope / out of scope).  
2. **Enumerate violations** present in the current code file (things that are in the file but out of scope for that boundary).

That keeps the rule honest without pretending the file is clean.

**Decompile only.** Listing “violations in this file” is a **side effect of lifting existing code**. It must not appear as a normal authoring pattern for greenfield meta.

**Compile prerequisite:** boundaries must be defined **cleanly, with no exception/violation list**. A leaf (or collection) that still carries decompile-era violations is **not compilable** until the meta is cleaned (split leaves, move responsibilities, or drop the violation list because the code/design was fixed). Compile must **refuse** rather than re-emit a kitchen sink under a violated boundary.

### 1.2 Two constraint surfaces (product vs architecture)

Top-down and developer concerns are **both** first-class; they sit at different depths of the same tree.

| Surface | Who typically writes | What constraints look like | Tree place |
|---------|----------------------|----------------------------|------------|
| **Product (BDD-like)** | Non-programmers and anyone stating intent | Behavior **by example** and/or **simple rules** (“when I press space, done flips”; “list survives restart”) | Upper **collections** and product-facing nodes |
| **Architecture** | Developers | Structure and modularization — especially **one leaf meta file ↔ one source file**, ownership, allowed dependencies | **Leaves** (and structural collections that only group those leaves) |

**Product surface (akin to BDD):**  
Specify *what must be true for the user* via examples and short rules. That is the non-programmer-accessible portion. It does **not** require naming modules or files. Compile (and lower meta) must not violate these constraints.

**Architecture surface:**  
Developers add constraints on *how the system is cut*: file boundaries, what a module owns, what it must not pull in. The MVP **1:1 leaf meta ↔ one code file** rule is the primary architectural constraint — it forces modularization to be explicit and decompilable.

```text
Product constraints (examples + rules)     ← BDD-like, often collections / upper nodes
        ↓ refine / attach
Architecture constraints (file-shaped leaves)  ← developer; 1 meta file : 1 code file
        ↓ compile
Source files
```

Neither surface should fully enumerate implementation. Product does not list helpers; architecture pins **file-level** ownership and contracts, not every internal function (unless a developer chooses finer leaves later).

A node may carry both kinds of constraint when useful (e.g. a leaf that is both “the store file” and “must persist after every change”), but authors should not force product people to invent file trees, or force every product rule into a leaf before architecture is designed.

---

## 2. MVP structural constraint (firm)

### 2.1 Leaf: one meta file → one code file

For **leaf** MetaCode nodes:

```text
one MetaCode file  compiles into  one actual source code file
```

That is the bottom of the hierarchy for MVP. No multi-file emit from a single leaf. No one leaf “is the whole app’s code.”

**Implications:**

- Modularize the meta tree so leaves match a sensible **code file** grain.  
- Compile runs are naturally **per leaf** (plus language def + skill; parents only as needed for context).  
- Tests for that file may live beside it or as the host project requires; the **primary** compile product of a leaf is **one code file**.

### 2.2 Collection (non-leaf) meta files

Not every meta file is a leaf. **Collection** (abstract) nodes group children:

| Kind | Compiles to code file? | Role |
|------|------------------------|------|
| **Leaf** | **Yes — exactly one** | Describes one code file’s responsibility and behavior |
| **Collection** | **No** (MVP) | Groups leaves / other collections; product or package overview; navigation in the tree |

Collections may later gain optional “index” or barrel emits; **MVP: collections do not emit code.** They organize and constrain.

Root files (e.g. `L0.Todo.md`) are typically **collections** until the tree is refined into file-shaped leaves.

### 2.3 Decompile (MVP: keep it that simple)

```text
one source code file  decompiles into  one leaf MetaCode file
```

- Declared sources that are code files each produce (or update) one leaf meta file.  
- Collections are built by **grouping** leaves (folders, packages, or explicit parent meta) — not by inventing a parallel taxonomy.  
- MVP does not require fancy multi-file fusion into one mega-meta.

### 2.4 Refine until leaves are file-shaped

Hierarchy above the leaves can follow user-facing or design cuts. Before implementer compile, **split/merge until each leaf is something you’d put in one code file.** If a node is still “the whole UI + store + keys,” it is not a leaf yet.

---

## 3. Who writes meta / who decides what

### 3.1 Constraints in meta; freedom at compile

| In MetaCode (constraints) | At compile (implied fill) |
|---------------------------|---------------------------|
| What this **file** is for and must guarantee | How it is implemented inside the file |
| Rules / invariants / refusals that matter | Algorithms, helpers, local types |
| Ownership boundaries (must / must not) | Frameworks and factoring within the file |
| Checks that prove the constraints | Extra tests compile invents to match |

If meta is silent, **compile decides** within the constraints and reports choices.  
If meta states a constraint, **compile must not violate it.**  
Do **not** require meta to list every function or step “so the model knows what to write.”

### 3.2 Format is deferred

Content and hierarchy first. Formal grammar later. Plain notes are fine.

### 3.3 User text vs Agent section (hard rule)

| Zone | Who writes | Holds |
|------|------------|--------|
| **User** (everything above `# Agent`) | Human author | Specifications |
| **`# Agent`** | Agents only | Assumptions, open questions, notes, child pointers |

**Agents must not modify user text.** Only edit under `# Agent`.  
If `# Agent` is missing, the agent may **append** it; never alter lines above.

---

## 4. Hierarchy

**Tree of meta files**, not one blob.

| Node kind | Typical content |
|-----------|-----------------|
| **Collection** | Purpose, **in/out scope**, shared constraints, list of children |
| **Leaf** | Purpose, **in/out scope** for **one** code file, decisive contracts; maps 1:1 at compile |

**Working-memory budget:** each file stays roughly one screen of real content. Split rather than thicken.

**Children** match modularization that can bottom out in **code files** (user-facing names OK at the top; file-shaped names as you near leaves).

---

## 5. What to say (content, not template)

Prefer **constraints and ownership** over inventories. No required heading list.

Useful: purpose, **in scope / out of scope**, must-hold rules, decisive controls, checks that prove the rules.  
Avoid: complete API rosters, play-by-play algorithms, “and also handle…” catalogs that follow from a tighter rule.  
Every file must answer **inside vs outside**; a purpose line alone is not enough if ownership is ambiguous.

**“What it is not”** is not a default section; a rare boundary constraint is fine when it prevents a real mistake.

For **leaves**: what this **one file** must own and guarantee — not every symbol inside it.

---

## 6. Other rules

### 6.1 No redundancy

Each fact once; refine in children.

### 6.2 Behavior and checks together

Same coin at the unit that owns the behavior (often the leaf).

### 6.3 Embed, don’t doc-drift

Code should reflect meta via naming/structure where possible.

### 6.4 Prefer clear over cryptic

Plain language when it works; precision when the author wants it.

---

## 7. Compile

### 7.1 Leaf compile (primary MVP op)

```text
compile_leaf(language_definition, leaf_meta [, parent_context])
  → one_code_file + tests_as_needed + compile_report
```

**Inputs:** language def; **one leaf** MetaCode file; compile skill; optional short parent collection(s) for context only.  
**Output:** **exactly one** source file (path recorded in report); plus report (choices, gaps).

**Must not:** emit multiple peer source files from one leaf; invent sibling modules that should be other leaves; treat missing helper lists as missing product constraints.

**Must:** satisfy stated constraints; invent only within them; report free choices.  
**Must refuse:** leaf meta that still documents **boundary violations** / exception lists from decompile — clean the meta (and design) first; compile only clean boundaries.

### 7.2 Collection compile (MVP)

Collections **do not** emit code. A “compile the app” workflow means: compile **each leaf** (separately or batched), using collections only as context/index.

### 7.3 Closed context

No ambient chat, no full SPEC, no undeclared repo files as hidden requirements.

---

## 8. Decompile

### 8.1 File decompile (primary MVP op)

```text
decompile_file(language_definition, one_code_file)
  → one_leaf_meta_file [+ unknowns]
```

**Inputs:** language def; **one** declared code file; decompile skill.  
**Output:** **one** leaf MetaCode file of **constraints and ownership** for that file (not a line tour or full API roster).

**Prefer:** purpose, **in/out scope** (intended boundary), invariants, decisive contracts, checks.  
**If the current code violates that boundary:** still state the boundary, then **enumerate violations** in this file (decompile-only pattern). Optional `# Agent`: needs split / proposed leaves.  
**Avoid (in user zone):** complete public-symbol dumps; those may sit under `# Agent` if useful for navigation.  
**Never treat violation lists as a normal greenfield style** — they exist only to describe legacy mess on the way to a clean tree.

### 8.2 Building the tree

After per-file leaves exist, add **collection** parents to group them (by folder, package, or human structure). MVP can be flat leaves first, collections second.

---

## 9. Repo layout (examples)

When a tree has multiple collections, prefer:

```text
examples/<name>/
  meta.md                 # product root (only meta at example root, when desired)
  README.md, reports…     # example chrome
  machine/                # emit sink (optional at root)
  src/                    # decompile-of-source body (this example); other exercises may use other folder names
    <collection>.md       # collection meta (sibling of directory)
    <collection>/         # children only
      <leaf>.md           # leaf named after module stem (items.md ↔ items.py)
```

- **Collection** = `name.md` **beside** `name/` (not inside it — avoids clashing with a leaf also called `name.md`).  
- Product `meta.md` need not peer with every collection; push collection pairs under a body dir (e.g. `src/` for decompiles).  
- **No layout prefixes** (`C.`, `L0.`, flat `leaves/` bags).  
- Need not mirror the original source tree.

---

## 10. Document control

| Version | Notes |
|---------|--------|
| 0.1–0.4 | Earlier stubs (budget, zones, non-programmer emphasis) |
| 0.5 | **MVP firm:** leaf meta file ↔ one code file; collections group only; decompile = one file → one leaf; non-programmer access = inspiration not hard rule |
| 0.6 | Meta = **constraints** (not full enumeration); compile fills implied decisions; decompile recovers constraints/ownership |
| 0.7 | Dual surfaces: product BDD-like (examples/rules) + developer architecture (leaf ↔ file) |
| 0.8 | Every node must define in/out scope and boundaries; kitchen-sink decompile may refuse or split |
| 0.9 | Decompile may list boundary violations under a clear intended boundary; compile requires clean boundaries (no exceptions) |
