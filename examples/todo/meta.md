# Full-screen todo editor

MetaCode for the first lang example. Hierarchical refinement tree.  
**Host stack:** TBD (declare before first compile; one stack only).

---

## Purpose

Provide a **full-screen todo editor**: a single focused application surface where a person manages personal todos without leaving the primary view. The product *is* the editor (list + item editing), not a multi-page app shell or CLI toolkit.

---

## Non-goals

- Multi-user / auth / sync / cloud backend  
- Labels, projects, GTD systems, calendars, notifications  
- Collaboration, sharing, comments  
- Mobile-native apps (responsive full-viewport web is OK if web stack chosen)  
- Plugin systems, themes marketplace, AI features inside the todo app  
- General notes or markdown documents  

---

## Architecture

### Runtime shape

- **Single process** (or single static web app) delivering one primary full-screen view.  
- **Local persistence** only for MVP (file or local DB / localStorage — choose one when host stack is fixed; name it here).  
- No required network service.

### Modules (skeleton names — compile must honor)

| Module | Responsibility |
|--------|----------------|
| `app` | Boot, full-screen shell, top-level layout |
| `todo_store` | Load/save todos; in-memory model; persistence boundary |
| `todo_list` | List rendering, selection, bulk-visible state |
| `todo_item_editor` | Inline or focused edit of a single todo’s fields |
| `commands` | User intents: add, edit, toggle complete, delete, maybe filter |
| `persistence` | Read/write the chosen local store |

*Do not add modules at compile time without updating this table.*

### Data flow

```text
commands → todo_store → persistence
                ↓
         todo_list / todo_item_editor (views)
```

---

## Surface

### Primary view

- Occupies the **full screen / full viewport** (terminal alternate screen or browser viewport).  
- Shows the todo list as the dominant UI.  
- Always-available path to **add** and **edit** without navigating to a separate app section.  
- Clear **selection** / focus model (keyboard-first preferred).

### Commands (user-visible intents)

| Intent | Behavior sketch |
|--------|-----------------|
| Add todo | Create item with empty or prompted title; focus for edit |
| Edit title | Change the selected (or targeted) todo’s title |
| Toggle complete | Flip completed flag; list reflects state |
| Delete | Remove todo after confirm **or** explicit destructive binding (pick one in elaborations; default: confirm once) |
| Filter (optional MVP+) | All / active / completed — only if it fits without clutter |

### Presentation rules

- Completed items remain visible but visually distinct (or filterable).  
- Empty state: explain how to add the first todo.  
- No unrelated chrome (settings pages, side nav forests).  

---

## Data / state

### Entity: `Todo`

| Field | Notes |
|-------|-------|
| `id` | Stable unique id (store-generated) |
| `title` | Non-empty string after commit of edit |
| `completed` | Boolean |
| `created_at` | Timestamp |
| `updated_at` | Timestamp |

### Invariants

- Every todo has a stable `id`.  
- Title is trimmed; empty title not committed (cancel or keep prior).  
- Persistence round-trip preserves all fields after restart.

### Persistence

- Single local store (path or key TBD with host stack).  
- Load on startup; save on each mutating command (or debounced — prefer simple reliable save-on-change for MVP).

---

## Behavior and tests

*Code and tests are one coin. Scenarios below are both product behavior and the checks a compile must emit.*

### Feature: Boot and empty state

- **Behavior:** On first launch with no store data, show empty state and affordance to add.  
- **Scenarios:**  
  - S1: Fresh store → UI shows empty state, not an error.  
  - S2: After add+restart → items reload from persistence.

### Feature: Add todo

- **Behavior:** User can add a todo with a title; it appears in the list; it is persisted.  
- **Scenarios:**  
  - S3: Add with title `"Buy milk"` → one item, not completed, listed.  
  - S4: Add then restart process/app → item still present.

### Feature: Edit title

- **Behavior:** User can change a todo’s title; update is shown and persisted.  
- **Scenarios:**  
  - S5: Edit title A → B → list shows B; restart keeps B.  
  - S6: Empty title commit rejected; previous title remains.

### Feature: Toggle complete

- **Behavior:** User can mark complete and uncomplete; visual state follows; persisted.  
- **Scenarios:**  
  - S7: Toggle complete → `completed == true`; restart keeps true.  
  - S8: Toggle again → active again.

### Feature: Delete

- **Behavior:** User can delete a todo; it disappears and stays gone after restart.  
- **Scenarios:**  
  - S9: Delete sole item → empty state.  
  - S10: Delete one of many → others unchanged.

### Feature: Full-screen editor UX

- **Behavior:** Primary workflow happens on one full-screen surface; focus/selection remains usable for keyboard-oriented flow.  
- **Scenarios:**  
  - S11: From list, user can add and edit without leaving the primary view.  
  - S12: (Manual OK) Resize / full viewport still shows list as primary content.

### Elaborations (explicit)

- **Delete confirm:** require a single confirmation step before delete (MVP).  
- **Ordering:** stable order by `created_at` ascending unless user reordering is added later (not in MVP).  

---

## Infrastructure

- None beyond local filesystem or local browser storage.  
- No database server, no Docker dependency for MVP.

---

## Open questions

- Host stack: TypeScript (web full-viewport vs terminal TUI) vs Python TUI?  
- Exact keybindings / mouse expectations?  
- Filter all/active/completed in MVP or post-MVP?  

---

## Compile notes (for skill)

- Emit into `examples/todo/machine/`.  
- Honor module table and `Todo` fields.  
- Emit automated tests for S1–S10 where the host allows; S11–S12 may be automated or manual per stack.  
- Do not add auth, sync, or extra entities.  
