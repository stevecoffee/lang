App name: Todo
Interface: Full-screen text app
Purpose/Behavior: shows a list of todo items
key bindings:
  arrows navigate
  shift arrow up/down reorders list items
  enter - toggles edit mode
  space toggles checkbox


# Agent

Level: L0 (product root)
Child: L1.md

## Assumptions
- One person, one machine; personal list (not multi-user)
- "Text app" means keyboard-first full-screen UI (terminal-style or similar)
- List items are todos with at least a title and a done state (checkbox)
- Arrows move a selection; shift+arrows move the selected item in the list
- Enter switches between normal viewing and editing the selected title
- Space flips done on the selected item

## Open questions
- How do you add a new todo?
- How do you delete a todo?
- How do you finish or cancel edit mode (only Enter is specified)?
- Does the list survive quitting and reopening?
- Any other keys (quit, help)?
- Exact look of a row beyond "checkbox" + title?

Agents: edit only under # Agent. Never change the user text above.
