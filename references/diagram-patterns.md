# Diagram Patterns

Use the smallest pattern that fits the task.

## Flowchart

Best for procedures, approvals, and operational steps.

- Choose one direction: top-to-bottom or left-to-right.
- Use 4 to 8 main nodes for a normal diagram.
- Keep at most 1 or 2 decision diamonds.
- Put terminal outcomes at the edges, not in the middle.
- Prefer one label per arrow only when the branch meaning is unclear.

Suggested structure:

1. Title
2. Start or input
3. Core steps
4. Optional decision
5. End states

## Architecture Diagram

Best for systems, services, integrations, and platform boundaries.

- Draw environment or domain containers first.
- Put user-facing entry points on the outside edge.
- Put core services in the center.
- Put data stores below or beside the services they support.
- Distinguish compute, storage, and external systems by color, not by many shapes.

Suggested structure:

1. Title
2. Outer boundaries
3. Entry points
4. Internal services
5. Data stores
6. External dependencies

## Relationship Diagram

Best for ownership, dependency, and concept mapping.

- Identify the primary node or group first.
- Keep line crossings low by clustering related peers.
- Use containers only when they add hierarchy.
- Keep labels noun-based and short.

Suggested structure:

1. Central concept or top layer
2. Adjacent domains
3. Secondary dependencies

## Interaction Overview

Best for lightweight sequence or message flow explanations.

- Keep only the key participants.
- Keep only the critical messages.
- Collapse repeated chatter into one labeled arrow.
- Prefer 4 to 6 interactions for a compact view.

Suggested structure:

1. Participants aligned horizontally
2. Messages flowing downward
3. Optional notes on the side, not between flows

## Escalation Rule

If the requested diagram is getting crowded:

- Reduce detail before increasing decoration.
- Merge minor nodes into grouped labels.
- Split one complex diagram into two smaller diagrams when the story naturally separates.
