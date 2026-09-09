---
name: flowchart-creator
description: Create or revise flowcharts, decision trees, process maps, workflow diagrams, and code-flow diagrams from prose, requirements, or source code. Use when the user asks for a flowchart or an editable Mermaid, Graphviz, ASCII, SVG, or PNG process diagram. Do not use for quantitative data charts or free-form illustrations.
---

# Flowchart Creator

Turn the user's material into a diagram that is accurate, readable, and easy to revise.

## Choose the deliverable

- Default to Mermaid `flowchart` source because it is portable and editable.
- Use Graphviz DOT, ASCII, or another requested notation when the user names it or the destination requires it.
- If the user requests SVG or PNG, render the diagram when an appropriate local tool is available. Keep the editable source alongside the rendered artifact.
- For a small diagram requested inline, return it directly in the response. Save files when the user requests an artifact or when the diagram is too large to use comfortably inline.

Do not ask about format or orientation when a sensible default will work. Use top-to-bottom for hierarchical or decision-heavy flows and left-to-right for timelines and pipelines. Ask a question only when missing domain logic would materially change the process.

## Build the flow

1. Identify the real start and end states, actions, decisions, inputs or outputs, subprocesses, loops, and failure paths.
2. Preserve the user's logic. Do not invent approvals, error handling, or business rules; surface material assumptions instead.
3. Use short action-oriented node labels. Phrase decisions as questions and label outgoing branches with meaningful conditions such as `Yes` and `No`.
4. Group phases or owners only when grouping improves comprehension. Split an overly dense process into a high-level overview and one or more detail diagrams.
5. Prefer a clear primary path, consistent branch direction, and few crossing edges. Add a legend only for notation that is not self-explanatory.

For code-flow diagrams, follow actual control flow, including early returns, loops, exceptions, and important asynchronous boundaries. Omit implementation details that do not affect the requested level of understanding.

## Write robust source

For Mermaid:

- Start with `flowchart TD` or `flowchart LR`.
- Give nodes stable, simple IDs separate from their displayed labels.
- Quote or escape labels containing punctuation that could be parsed as syntax.
- Use conventional shapes consistently: rounded terminals, rectangles for actions, diamonds for decisions, and parallelograms for input or output when useful.
- Avoid styling unless it materially clarifies states, ownership, risk, or the primary path.

For revisions, preserve stable node IDs and the user's chosen format unless changing them is necessary to satisfy the request.

## Verify and deliver

- Check that every nonterminal node has an appropriate outgoing path and every branch can reach an end, retry, or explicitly marked unresolved state.
- Check branch labels, loops, and ordering against the source material.
- Parse or render the source when a compatible tool is available, then inspect the result for clipped labels, overlaps, and unreadable routing.
- Return the editable source and any rendered artifact. Briefly state important assumptions or omitted detail; do not narrate routine construction steps.
