# Notebook Style Guide

The final deliverable is executed Jupyter notebooks. The instructor will probably inspect the executed notebooks more than rerun them, so outputs must remain visible and readable.

## General style

Use a clear educational flow:

1. Introduce the task.
2. Explain the dataset.
3. Explain the method.
4. Run the code.
5. Show tables/plots.
6. Interpret results.
7. Include `How I solved this task`.
8. Mention limitations.

## Required subsection for every task

Every task must include this exact heading:

```markdown
### How I solved this task
```

This section should explain:

- What was done.
- Which algorithm/tool was used.
- Why it was selected.
- What the result means.

## Code style

- Keep code readable.
- Use short helper functions only when reused.
- Avoid hiding assignment logic in external modules.
- Prefer explicit notebook cells over clever abstractions.
- Add comments for non-obvious steps.
- Use deterministic random seeds where sampling is used.

## Plot style

Every plot must have:

- Title.
- Axis labels.
- Readable size.
- Legend when needed.
- Short interpretation below it.

Save figures to:

```text
exports/figures/
```

## Tables

Use pandas DataFrames for ranked results. Sort clearly. Show enough rows for interpretation but avoid huge tables.

## Expensive computation

When a calculation is expensive:

- sample/filter the graph;
- cache intermediate results;
- document the exact method;
- explain what the sampling may miss.

## Manual screenshots

For Cytoscape/Gephi tasks, include placeholder markdown cells if screenshots must be inserted manually later.

Example:

```markdown
### Gephi screenshot
TODO: Insert screenshot here after opening `exports/gephi/selected_movie.gexf` in Gephi.
```
