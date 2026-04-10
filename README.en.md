# Excalidraw Diagram Skill

Chinese version: [README.md](C:/work/codes/Art/excalidraw-diagram-skill/README.md)

A general-purpose Excalidraw skill for AI coding agents.  
It helps agents generate clean, editable, good-looking `.excalidraw` files and provides lightweight PNG export guidance.

## What It Does

- Creates flowcharts, architecture diagrams, module maps, component diagrams, and interaction overviews
- Supports two visual modes:
  - `normal`: cleaner and more formal
  - `hand-drawn`: keeps the Excalidraw sketch feel while staying readable
- Outputs complete `.excalidraw` JSON files, not partial fragments
- Reduces text clipping and border collisions
- Uses bound arrows so connectors stay attached when nodes move
- Provides PNG export guidance without relying on rendering scripts

## Good Fit For

- Codex, Claude Code, Cursor, Cline, OpenCode, and similar agents
- Workflows that need editable Excalidraw source files
- Teams that want consistent diagram style and fewer Excalidraw interaction issues

## Repository Layout

- [SKILL.md](C:/work/codes/Art/excalidraw-diagram-skill/SKILL.md): main skill definition
- [references](C:/work/codes/Art/excalidraw-diagram-skill/references): style rules, diagram patterns, output checks
- [examples](C:/work/codes/Art/excalidraw-diagram-skill/examples): example files, with both normal and hand-drawn variants for each diagram type

## How To Use

Using Codex as an example, explicitly reference the skill path and describe the diagram type, content, style, and desired output file.

Example 1: normal architecture diagram

```text
Use the excalidraw-diagram-skill at C:\work\codes\Art\excalidraw-diagram-skill.
Generate a normal-style system architecture diagram.
Include: Web Client, API Gateway, Core Service, Database.
Return a complete .excalidraw file named architecture.excalidraw.
```

Example 2: hand-drawn flowchart

```text
Use the excalidraw-diagram-skill at C:\work\codes\Art\excalidraw-diagram-skill.
Generate a hand-drawn approval flowchart.
Include: submit request, manager review, publish result.
Return a complete .excalidraw file and add PNG export guidance.
```

Example 3: module map with longer labels

```text
Use the excalidraw-diagram-skill at C:\work\codes\Art\excalidraw-diagram-skill.
Generate a normal-style module map.
Make sure longer labels do not clip and connectors remain attached when nodes move.
Return a complete .excalidraw file.
```

## Tips

- Say `hand-drawn` explicitly when you want the sketch look
- Say `normal` or `formal` when you want a clean documentation style
- If nodes should stay movable, mention that connectors must stay bound
- If you need PNG, generate `.excalidraw` first, then export from Excalidraw

## Examples

- Flowchart hand-drawn: [flowchart-basic.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/flowchart-basic.excalidraw)
- Flowchart normal: [flowchart-normal.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/flowchart-normal.excalidraw)
- Architecture normal: [architecture-basic.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/architecture-basic.excalidraw)
- Architecture hand-drawn: [architecture-hand-drawn.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/architecture-hand-drawn.excalidraw)
- Module map normal: [module-map-basic.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/module-map-basic.excalidraw)
- Module map hand-drawn: [module-map-hand-drawn.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/module-map-hand-drawn.excalidraw)
