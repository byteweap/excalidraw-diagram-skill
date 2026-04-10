# Style Recipes

Default to restrained, consistent styling. Support two explicit modes.

## Style Modes

### `normal`

- `roughness: 0`
- `strokeWidth: 2`
- `fontFamily: 3` first, `2` second
- Use tighter alignment and cleaner right angles
- Best for architecture, dependency, and formal documentation diagrams

### `hand-drawn`

- `roughness: 1`
- `strokeWidth: 2` or `2.5`
- `fontFamily: 1`
- Keep the same layout discipline, but allow a visible sketch feel
- Best for flows, brainstorming diagrams, and less formal visual explanations

Do not use strong sketchiness to hide a weak layout. The board still needs to read cleanly.

## Palette

Use one neutral stroke color across most elements:

- Primary stroke: `#1f2937`
- Secondary stroke: `#475569`
- Soft label text: `#64748b`

Use no more than four fills:

- Blue: `#dceafe`
- Green: `#dcf3e4`
- Amber: `#feefc8`
- Rose: `#fbe2e2`

For flowcharts, especially hand-drawn ones, prefer one slightly deeper step than the defaults above while staying muted:

- Flow blue: `#c6dbff`
- Flow green: `#cdebd8`
- Flow amber: `#fde2a7`

Use container fills sparingly and keep them lighter than node fills:

- Container blue: `#f1f7ff`
- Container gray: `#f1f5f9`

## Typography

- Main title: 28 to 34 px
- Section title: 20 to 24 px
- Node label: 18 to 22 px
- Small annotation: 14 to 16 px

Prefer code or sans fonts for a cleaner look:

- `fontFamily: 3` for clean labels
- `fontFamily: 2` if a softer sans look fits better
- `fontFamily: 1` for explicit hand-drawn requests

## Node Sizing

Keep siblings visually consistent.

- Small node: `160 x 64`
- Standard node: `200 x 84`
- Wide service node: `240 x 84`
- Decision diamond: `190 x 130`
- Long-label node: `240 x 96`

## Text Safe Area

Do not place text flush against borders.

- Rectangle safe padding: `16` to `24` px on all sides
- Container header top padding: at least `20` px
- Container header bottom gap before first node: at least `28` px
- Diamond text should stay inside the middle 55% to 65% width zone
- Arrow labels should be offset at least `12` px from the line
- Text element width should include extra slack beyond the visible text, instead of hugging the exact glyph width
- Single-line text elements should use a height larger than the theoretical minimum
- Multi-line text elements should reserve extra bottom space for edit mode

Resolve crowding in this order:

1. Increase node width or height
2. Rewrite the label shorter
3. Reduce font size by one step

Do not reduce font size first for standard nodes.

## Spacing

- Between title and content: 48 to 72 px
- Between containers: 96 to 140 px
- Between nodes in a row: 56 to 96 px
- Between rows: 64 to 110 px
- Inner container padding: 32 to 40 px

## Connectors

- Use `strokeWidth: 2`
- Use `roughness: 0` in `normal`
- Use `roughness: 1` in `hand-drawn`
- Keep arrows mostly horizontal or vertical
- Avoid multi-bend connectors unless routing is necessary
- Use muted connector color instead of pure black for dense diagrams

## Containers

Use containers only when they clarify ownership, domains, or layers.

- Give each container a header
- Keep headers aligned
- Use low-contrast fill
- Use thin but visible borders

## Titles And Labels

- Use one main title only
- Avoid subtitles unless the diagram needs a scope note
- Prefer verbs in flowcharts and nouns in architecture diagrams
- Rewrite long labels into shorter phrases before enlarging nodes
- For long but necessary labels, enlarge the node instead of letting text touch the border
- Use one size smaller text inside diamonds than inside wide service nodes
- Do not hand-author text boxes with pixel-tight width and height values
