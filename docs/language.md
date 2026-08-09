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

### 3.1 Product vs implementation

| In MetaCode | At compile (for a leaf) |
|-------------|-------------------------|
| What this **file’s** code is for | Frameworks, idioms inside that file |
| Behavior and rules this file must honor | Exact algorithms, types, helpers |
| Public surface this file exposes (if stated) | Private helpers within the file |
| Checks that apply to this unit | How tests are wired in the host layout |

If meta is silent on implementation inside the file, **compile decides** and reports choices.  
If meta states a rule, **compile must not drop it.**

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
| **Collection** | Name, purpose of the group, list of children, constraints that apply to the whole |
| **Leaf** | Enough to implement **one** code file; maps 1:1 at compile |

**Working-memory budget:** each file stays roughly one screen of real content. Split rather than thicken.

**Children** match modularization that can bottom out in **code files** (user-facing names OK at the top; file-shaped names as you near leaves).

---

## 5. What to say (content, not template)

Prefer **positive** description. No required heading list.

Useful: what it is, what it does, controls/rules that matter, checks.  
**“What it is not”** is not a default section.

For **leaves**, also useful: what this code file owns vs what it calls/imports (in plain language).

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

**Must not:** emit multiple peer source files from one leaf; invent sibling modules that should be other leaves.

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
**Output:** **one** leaf MetaCode file describing that code file’s role and behavior (not a line-by-line paste).

### 8.2 Building the tree

After per-file leaves exist, add **collection** parents to group them (by folder, package, or human structure). MVP can be flat leaves first, collections second.

---

## 9. Repo layout (examples)

```text
examples/<name>/
  L0.*.md          # often a collection (product root)
  …                # further collection / leaf meta files
  machine/         # emitted code files (one per compiled leaf)
```

---

## 10. Document control

| Version | Notes |
|---------|--------|
| 0.1–0.4 | Earlier stubs (budget, zones, non-programmer emphasis) |
| 0.5 | **MVP firm:** leaf meta file ↔ one code file; collections group only; decompile = one file → one leaf; non-programmer access = inspiration not hard rule |
