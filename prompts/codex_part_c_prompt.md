# Codex Prompt — Part C

Read `AGENTS.md`, `docs/dataset_setup.md`, `docs/notebook_style_guide.md`, `docs/git_workflow.md`, and `docs/part_c_instructions.md` before coding.

Work on branch `part-c`.

Implement and execute `notebooks/part_c.ipynb` for Enron manager detection and local LLM analysis.

Important requirements:

- Use the student's filled manual selections in `docs/part_c_instructions.md`.
- Stop if any required manual selection is empty.
- Keep important code inside the notebook.
- Apply exactly three selected centrality algorithms.
- Compute precision@10 if manager labels are available.
- Use only a local LLM.
- Do not call external LLM APIs.
- Verify Ollama/model availability before attempting LLM calls.
- Include the exact LLM prompts used.
- Sample and truncate emails before passing them to the local LLM.
- Include local LLM classifications and role summaries.
- Visualize the Enron network or a meaningful subgraph.
- Include `How I solved this task` for every task.
- Execute the notebook and keep outputs.
- Commit progress frequently.
- Push branch and open PR if possible.

At the end, print:

1. Enron files used.
2. Centrality algorithms used.
3. Top-10 results per algorithm.
4. Label/precision@10 status.
5. Local LLM tool/model used.
6. Users analyzed with LLM.
7. Git branch/commit/PR status.
