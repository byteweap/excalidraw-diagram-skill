# Output Checklist

Run this pass before returning the final result.

## File Validity

- The output is complete JSON, not a fragment.
- The top-level fields include `type`, `version`, `source`, `elements`, `appState`, and `files`.
- The file can be saved directly with the `.excalidraw` suffix.

## Readability

- The diagram has one obvious reading direction.
- Titles, groups, and nodes form a clear hierarchy.
- Text does not overlap with shapes or connectors.
- Text does not touch or visually press against borders.
- Double-clicking a text label in Excalidraw should not reveal a clipped text box.
- Arrowheads and labels remain readable at normal zoom.
- Container headers have their own vertical space.
- Diamond labels stay inside the safe central area.
- Arrows between nodes are bound, not floating, so dragging a node keeps the connector attached.

## Visual Quality

- The palette stays within the allowed limited range.
- Similar nodes share similar size and styling.
- Containers add meaning instead of clutter.
- The canvas has enough whitespace around the content.
- The selected style is consistent: either clearly `normal` or clearly `hand-drawn`.

## Content Discipline

- The diagram includes only information needed for the stated goal.
- Repeated or minor details are grouped instead of expanded into many nodes.
- Decorative elements have been removed if they do not improve comprehension.
- If labels feel crowded, node size was increased before shrinking text.

## PNG Guidance

If PNG is requested, the response also includes:

- Open in Excalidraw
- Export as PNG
- Crop to content
- Prefer 2x or 3x scale
- Choose white or transparent background based on use
