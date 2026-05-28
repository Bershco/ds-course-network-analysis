# Codex Prompt — Part B

Read `AGENTS.md`, `docs/dataset_setup.md`, `docs/notebook_style_guide.md`, `docs/git_workflow.md`, and `docs/part_b_instructions.md` before coding.

Work on branch `part-b`.

Implement and execute `notebooks/part_b.ipynb` for directed link prediction.

Important requirements:

- Use the student's filled manual selections in `docs/part_b_instructions.md`.
- Stop if any required manual selection is empty.
- Keep important code inside the notebook.
- Define positive and negative directed link examples clearly.
- Implement the selected train/test split strategy.
- Implement a topology-based baseline classifier.
- Implement an improved classifier using embeddings or link features.
- Report selected metrics.
- Include the bonus future link prediction only if enabled and timestamps exist.
- Include `How I solved this task`.
- Execute the notebook and keep outputs.
- Commit progress frequently.
- Push branch and open PR if possible.

At the end, print:

1. Dataset used.
2. Number of nodes/edges.
3. Positive/negative example counts.
4. Baseline metrics.
5. Improved model metrics.
6. Bonus status.
7. Git branch/commit/PR status.
