# MetaCode — language definition (loadable)

**Status:** stub / Phase 1 (content first; format later)  
**Audience:** anyone describing software in plain language; agents on compile/decompile runs  
**Not this file:** product phases, Keep, chrome — see `SPEC.md` (do **not** load SPEC into a pure compile run).

Working names: **MetaCode**, **MetaCompiler** / compile skill, **MetaBDD**. Better names TBD.

---

## 1. Thesis

**Meta is source. AI write is compile. Classic code is machine language.**

| Layer | Who it’s for | Role |
|-------|----------------|------|
| **MetaCode** | Humans (including **non-programmers**) | What the system is and does — hierarchical, plain language |
| **Compile** | LLM / later tools | Turn meta into classic code + tests; **fill in implementation** |
| **Classic code** | Machines and programmers when needed | Runnable result |

Meta is **not** a programming language in disguise. If only engineers can write it, we failed.

---

## 2. Who writes meta / who decides what

### 2.1 Accessible to non-programmers

Authors describe **intent, behavior, and experience** in ordinary language (and simple structure).

They should **not** need to specify:

- modules, packages, file layout  
- frameworks, types, storage engines  
- algorithms, unless the *product* cares about a particular approach  

Those are **implementation details**. The compile step (LLM today) chooses them, records choices in a compile report, and must still honor anything the meta *did* state.

### 2.2 What belongs in meta vs compile

| In MetaCode (author) | At compile (LLM / tool) |
|----------------------|-------------------------|
| What the thing is | How files and modules are cut |
| What someone can do | Frameworks, libraries, idioms |
| What they see / press / say | Exact data schema (unless author stated it) |
| Rules that matter to the user (“empty title doesn’t stick”) | Algorithms and internal APIs |
| Durable facts (“still there after restart”) | Host language details (unless author fixed them) |

If meta is silent on an implementation choice, **compile decides** — do not force the author to invent programmer structure to get a build.

If meta states a product rule, **compile must not “improve” it away**.

### 2.3 Format is deferred

Nail **content and hierarchy** first. Do **not** block on markdown style, required headings, or formal grammar.

Plain notes, lists, keybindings, short prose — all fine while we learn what matters. Formalize spelling/shape later.

---

## 3. Hierarchy (core, not optional)

**Vision:** MetaCode is a **tree of units**, not one giant file that describes everything.

| Level | Holds |
|-------|--------|
| **Root** | Whole product in one breath — name, kind, main experience |
| **Children** | One concern each (e.g. list navigation, editing, saving) when that concern needs room |
| **Deeper** | Only when working that slice |

Same spirit as small code files: **one mental page per node**. Detail goes **down** into children, not into a longer root essay.

### 3.1 For now (before multi-file)

We may keep a single file and use **sections as stand-ins for child nodes**.

Treat a clear section as a future file/node. When content outgrows working memory, **split** (section → file) rather than keep growing one blob.

Do **not** treat “one `meta.md` for the whole app forever” as the design.

### 3.2 Working-memory budget (per node)

Per **node** (file later; section or file now):

| Budget | Guideline |
|--------|-----------|
| Length | About one screen when skimming |
| Ideas on the page | Only what you need for **this** unit right now |

If it doesn’t fit, it’s a signal to **add a child**, not to write denser jargon.

### 3.3 Compile and hierarchy

Compile may run on **one subtree** (one node + what it needs from parents). Parent gives context; child owns local detail. Avoid loading an entire monorepo-sized meta into one run when a branch will do.

---

## 4. What to say (content, not template)

No required section list. Prefer **positive** description.

Useful kinds of content (use only what helps):

- **What it is** — short  
- **What you can do** — behaviors  
- **How it feels / controls** — e.g. keybindings, layout in user terms (“full-screen list”)  
- **Rules that matter** — user-visible constraints  
- **Checks** — often “the does-list works,” including after restart if that matters  

**“What it is not”** is **not** a default section. Long exclusion lists are usually an anti-pattern. Prefer a clear positive description. A rare, local “not X” is fine when the positive wording would otherwise mislead.

Avoid: scenario ID catalogs, module maps, and programmer scaffolding unless a **programmer author** deliberately wants them in a **child** node about implementation.

---

## 5. Other hard rules

### 5.1 No redundancy

Say each fact once. Refine in children; don’t copy the same rule everywhere.

### 5.2 Behavior and checks together

What it does and how we know it works stay close (same coin). No parallel “test novel” required. Obvious checks can be implied (“still works after restart”).

### 5.3 Embed, don’t doc-drift

When code exists, prefer names/structure that reflect meta over a second hand-maintained doc tree.

### 5.4 Prefer plain over cryptic

Words a non-programmer would use. No fake precision.

---

## 6. Compile

```text
compile(language_definition, metacode_unit) → machine_code + tests + compile_report
```

**Inputs only:** this language definition; the MetaCode unit (node/subtree); the compile skill.  
**Not inputs:** full SPEC, ambient chat, undeclared repo files, “also remember…”

**Compile must:**

1. Treat meta as **product truth**; fill **implementation** where meta is silent.  
2. Honor explicit user-facing rules and described controls.  
3. Emit tests from stated/implied behavior.  
4. Report implementation choices, gaps, and questions — especially decisions a non-programmer never wrote down.

**Brownfield** (meta + existing code + reconcile) is a separate mode later.

---

## 7. Decompile

```text
decompile(language_definition, declared_sources) → metacode_tree [+ unknowns]
```

**Inputs only:** language definition; declared sources; decompile skill.

**Decompile must:**

1. Produce **hierarchical** meta (root + children as needed), plain language first.  
2. Capture user-facing behavior and shape — not a code tour.  
3. Stay within working-memory budget per node; split instead of one giant file.  
4. Leave implementation detail out of meta unless it is truly product-level.  
5. Mark unknowns rather than inventing product facts.

---

## 8. Repo layout (examples)

- Examples: `examples/<name>/`  
- Meta today: `examples/<name>/meta.md` (sections ≈ future nodes; multi-file tree later)  
- Emit: `examples/<name>/machine/`  

---

## 9. Document control

| Version | Notes |
|---------|--------|
| 0.1 | Initial stub |
| 0.2 | Working-memory budget |
| 0.3 | Non-programmer audience; LLM owns implementation detail; hierarchy as multi-node tree (sections as stand-in); format deferred; “not this” not default |
