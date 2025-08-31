# How it works

This project is intentionally minimal: a single `index.html` contains HTML, CSS, and JavaScript.
Below is a high‑level walkthrough of the major pieces and where to look in the source.

## App shell

- Tabs route between **Playground**, **Missions**, and **About** using a tiny router (`Nav.go(page)`).
- The visual style is pure CSS with a small palette and glassy panels.

## Blocks → Workspace

- The left **palette** contains `.block` elements with `data-op` attributes (e.g., `move`, `turn`, `repeat`).
- Dragging a palette block serializes a lightweight payload to `dataTransfer` with the block’s HTML and metadata.
- Dropping into the **stack** container reconstructs the block and adds small tools (up/down/delete).
- Nested blocks (e.g., `repeat`, `forever`) append a nested `.stack` to hold child blocks.

### Serialization

`Stack.serialize()` walks the workspace DOM and produces a JSON‑like program:

```json
[
  {"op":"whenFlag"},
  {"op":"repeat","args":[5],"children":[{"op":"move","args":[10]},{"op":"turn","args":[15]}]}
]
```

## Interpreter (Runner)

- `Runner.run()` resets state and executes the serialized program.
- Each block maps to a behavior in `execNode(node)` (move/turn/goto/say/color/wait/repeat/forever).
- Execution pushes entries into a `trace` used later by goal checkers.
- The **stage** is an HTML `<canvas>`; the sprite is rendered as a friendly circle with eyes.

### Arrow‑key input

The stage listens for keydown events:

- `↑` moves forward
- `↓` moves backward
- `←/→` rotate by 10°

These controls are always on, useful for exploration and certain missions.

## Missions & Goals

- Missions are defined in a `LESSONS` array (25 entries).
- Each mission has `{ id, title, sample, goal, md, check }`.
- When a run completes, `Goals.evaluate(trace, state, prog)` calls the mission’s `check` to set status.

**Examples of checks:**

- “Used `repeat` inside a loop”
- “Turned about 144° at least once in a 5‑repeat”
- “Visited 3 different coordinates with `goto`”

## Minimal Markdown renderer

Mission copy is written in tiny Markdown and converted to HTML via `renderMD` (headings, bold/italic, inline code, and bullets).

## Where to start reading the code

1. **Drag & Drop:** `// --------- Drag & Drop Blocks ---------`
2. **Stack & Serialization:** `// --------- Workspace Stack & Serialization ---------`
3. **Interpreter:** `// --------- Runner (Interpreter) ---------`
4. **Missions:** `// --------- MISSIONS (25) ---------`