---
name: excalidraw
description: Create concise, polished Excalidraw diagrams as complete .excalidraw JSON files and provide lightweight PNG export guidance. Use when an agent needs to produce flowcharts, architecture diagrams, component maps, relationship diagrams, process overviews, or interaction diagrams for Codex, Claude Code, Cursor, Cline, OpenCode, or similar agent runtimes without relying on renderer scripts.
---

# Excalidraw Diagram Skill

Create diagrams that are easy to open, easy to read, and easy to export.

## Workflow

1. Clarify the diagram goal, audience, and granularity.
2. Choose the simplest diagram type that communicates the idea.
3. Plan the layout before writing elements.
4. Output a complete `.excalidraw` JSON file, not only an `elements` array.
5. If PNG is requested, add short manual export guidance after the JSON.

If the runtime can write files, save the result directly as `<name>.excalidraw`.
If it cannot write files, return the full JSON so the user can save it unchanged.

## Style Modes

Default to `normal` style unless the user explicitly asks for a hand-drawn look.

- Switch to `hand-drawn` when the request mentions `手绘`, `草图`, `sketchy`, or `hand-drawn`.
- Use `normal` when the request mentions `普通`, `专业`, `规整`, `clean`, or `formal`.
- Do not infer style only from diagram type unless the user asks you to.

### `normal`

- Optimize for a clean professional look.
- Prefer `roughness: 0`.
- Prefer `fontFamily: 3` or `2`.
- Keep alignment strict and spacing regular.

### `hand-drawn`

- Keep the layout clean, but restore the Excalidraw sketch feel.
- Prefer `roughness: 1`; use `2` only when the user clearly wants a stronger sketch effect.
- Prefer `fontFamily: 1`.
- Allow slightly softer alignment and more organic connector lines.

For both modes:

- Use 3 to 4 fill colors at most.
- Keep saturation low and contrast readable.
- Keep node sizes consistent within the same group.
- Align nodes to a readable grid.
- Leave generous whitespace between groups.
- Use short labels, usually 2 to 6 words.
- Keep connectors straight or with a single bend when possible.
- Avoid decorative shapes unless they add meaning.

Read [references/style-recipes.md](references/style-recipes.md) when choosing spacing, colors, typography, or container patterns.

## Diagram-Type Guidance

- Flowchart: Arrange top-to-bottom or left-to-right. Use decision diamonds sparingly.
- Architecture diagram: Draw boundaries first, then services, then data flow.
- Relationship diagram: Establish hierarchy first, then connect dependencies.
- Interaction or sequence-style overview: Keep only key participants and key messages.

Read [references/diagram-patterns.md](references/diagram-patterns.md) for compact patterns by diagram type.

## Output Requirements

Always return a complete `.excalidraw` document with these top-level fields:

- `type`
- `version`
- `source`
- `elements`
- `appState`
- `files`

Prefer a minimal, standard structure that Excalidraw can open directly.
Do not depend on private runtime fields or repository-local scripts.

Use a skeleton like this as the starting point:

```json
{
  "type": "excalidraw",
  "version": 2,
  "source": "https://excalidraw.com",
  "elements": [],
  "appState": {
    "viewBackgroundColor": "#ffffff",
    "gridSize": null
  },
  "files": {}
}
```

## Element Rules

- Use rectangles for normal steps, services, and modules.
- Use diamonds only for decisions.
- Use text elements for titles, subtitles, and labels.
- Use arrows for directional flow.
- Use large low-contrast rectangles as containers for domains or layers.
- When an arrow connects two movable nodes, bind it to both nodes instead of leaving it free-floating.

Prefer a small set of reusable element patterns:

```json
{
  "type": "rectangle",
  "x": 120,
  "y": 120,
  "width": 200,
  "height": 84,
  "strokeColor": "#1f2937",
  "backgroundColor": "#e8f0fe",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "roughness": 0,
  "roundness": { "type": 3 },
  "opacity": 100
}
```

```json
{
  "type": "text",
  "x": 156,
  "y": 150,
  "text": "API Service",
  "fontSize": 20,
  "fontFamily": 3,
  "textAlign": "center",
  "verticalAlign": "middle",
  "strokeColor": "#111827",
  "backgroundColor": "transparent"
}
```

```json
{
  "type": "arrow",
  "x": 0,
  "y": 0,
  "points": [[0, 0], [140, 0]],
  "strokeColor": "#475569",
  "strokeWidth": 2,
  "roughness": 0,
  "startBinding": {
    "elementId": "source-node",
    "focus": 0,
    "gap": 1,
    "fixedPoint": null
  },
  "endBinding": {
    "elementId": "target-node",
    "focus": 0,
    "gap": 1,
    "fixedPoint": null
  },
  "endArrowhead": "arrow"
}
```

Use complete element objects in the final file, including ids, versions, seeds, and required geometry fields.

For every bound arrow:

- Set `startBinding` and `endBinding` on the arrow.
- Add the arrow id to each connected shape's `boundElements`.
- Do not use a free-floating arrow between movable nodes unless the user explicitly wants a detached annotation.
- Leave enough gap between connected nodes so Excalidraw can resolve the edge connection cleanly.

## Text Safety Rules

Treat text placement as a hard constraint, not a cosmetic detail.

- Keep at least 16 px of padding between text and a rectangle border.
- Prefer 20 to 24 px padding for titles inside containers.
- Use a more conservative text box inside diamonds; keep text centered in the widest middle area.
- Do not place text by simply centering a rectangle-sized text box over a diamond.
- Keep arrow labels offset from the line and arrowhead.
- Keep container headers separated from the top border and from the first row of nodes.
- Do not size a text element to the exact visible glyph bounds. Leave extra width and height so Excalidraw edit mode does not clip the text box when the user double-clicks.
- For single-line labels, keep a small width reserve and a taller line box than the bare minimum.
- For multi-line labels, keep extra height beyond the visible lines.

When text starts to feel crowded, resolve it in this order:

1. Expand node width or height.
2. Shorten the label.
3. Slightly reduce font size.

Do not shrink text first just to preserve a crowded layout.

## Layout Rules

- Keep four visual layers at most: title, containers, nodes, connectors.
- Use one primary reading direction.
- Keep group headers near the top-left of each container.
- Reserve dedicated top padding for container headers.
- Separate peer groups with at least 80 px.
- Separate nodes within a group with at least 48 px.
- Widen the canvas instead of stacking too many crossings.
- Split dense systems into 2 to 4 containers instead of one crowded board.
- Use larger nodes for labels longer than 2 or 3 words.
- Use smaller font sizes for diamonds and narrow nodes than for wide service blocks.

## What To Avoid

- Do not return pseudocode instead of `.excalidraw` content.
- Do not use many colors, gradients, or random styles.
- Do not rotate elements unless absolutely necessary.
- Do not place paragraphs inside nodes.
- Do not create tangled connectors if a container split would simplify the diagram.
- Do not add sketch noise when the goal is a clean professional output.

## PNG Export

This skill does not render PNG by script.

If the user requests PNG, provide the `.excalidraw` file first, then give a short note:

1. Open the file in Excalidraw.
2. Export as PNG.
3. Use "crop to content".
4. Prefer 2x or 3x scale.
5. Use a white background for documents and transparent background for overlays if needed.

Keep the export guidance brief.

## Self-Check

Before returning the result, verify:

- The JSON is complete and syntactically valid.
- The file can be saved directly as `.excalidraw`.
- The selected style matches the user's explicit request, or falls back to `normal` when unspecified.
- The layout has a clear reading order.
- Labels are short and non-overlapping.
- Text has visible safety padding from borders.
- Text boxes themselves have enough width and height reserve for Excalidraw edit mode.
- Diamond labels sit inside the safe center area.
- Arrow labels do not collide with lines, nodes, or arrowheads.
- Connected arrows remain attached when nodes are dragged inside Excalidraw.
- The palette is limited and consistent.

Read [references/output-checklist.md](references/output-checklist.md) for the final pass.

## Examples

Read these only when a concrete example would help:

- Flowchart hand-drawn: [examples/flowchart-basic.excalidraw](examples/flowchart-basic.excalidraw)
- Flowchart normal: [examples/flowchart-normal.excalidraw](examples/flowchart-normal.excalidraw)
- Architecture normal: [examples/architecture-basic.excalidraw](examples/architecture-basic.excalidraw)
- Architecture hand-drawn: [examples/architecture-hand-drawn.excalidraw](examples/architecture-hand-drawn.excalidraw)
- Module map normal: [examples/module-map-basic.excalidraw](examples/module-map-basic.excalidraw)
- Module map hand-drawn: [examples/module-map-hand-drawn.excalidraw](examples/module-map-hand-drawn.excalidraw)
