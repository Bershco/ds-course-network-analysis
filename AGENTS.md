# AGENTS.md — Network Analysis Assignment Codex Instructions

You are Codex CLI working inside a Linux VM on a university course assignment repository.

Your job is to implement, execute, document, and version-control a complete network analysis assignment using Jupyter notebooks.

The course lecturer expects the student to understand what was done. Therefore, every implemented method must be explained clearly in the notebook before and after the code. Do not only produce working code; produce understandable, educational work.

## Absolute priorities

1. Produce one executed Jupyter notebook per main part:
   - `notebooks/part_a.ipynb`
   - `notebooks/part_b.ipynb`
   - `notebooks/part_c.ipynb`
   - `notebooks/optional_practice.ipynb`
2. Keep all important assignment code inside the notebooks.
3. Use external `.py` files only for genuinely reused helper functions, and only when this makes the notebooks clearer.
4. Create and use a project-local virtual environment.
5. Install missing Python packages only inside that venv. Never use `sudo` for Python packages.
6. Execute notebooks and keep outputs visible.
7. Commit work frequently to Git.
8. Work on feature branches, push to GitHub, and open PRs if the GitHub remote is configured and authentication works.
9. Never commit raw datasets.
10. Never force-push or rewrite Git history.

## Manual selections already made by the student

Before starting a part, inspect the matching file under `docs/` and confirm that all `MANUAL_SELECTION_REQUIRED` placeholders were filled by the student.

If a required placeholder is still empty, stop and print a clear list of the missing fields. Do not invent student choices.

## Repository structure

Use this structure unless it already exists:

```text
network-analysis-assignment/
├── AGENTS.md
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   ├── raw/
│   │   ├── movie_dynamics/
│   │   ├── directed_network/
│   │   ├── enron/
│   │   └── chess/
│   └── processed/
├── notebooks/
│   ├── part_a.ipynb
│   ├── part_b.ipynb
│   ├── part_c.ipynb
│   └── optional_practice.ipynb
├── exports/
│   ├── gephi/
│   ├── cytoscape/
│   └── figures/
├── docs/
└── prompts/
```

## Environment setup

Create a venv at:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip wheel setuptools
python -m pip install -r requirements.txt
```

If `requirements.txt` is missing, create it with the packages actually used.

Recommended packages include:

```text
jupyter
notebook
jupyterlab
ipykernel
nbconvert
nbformat
pandas
numpy
scipy
matplotlib
seaborn
networkx
scikit-learn
python-louvain
igraph
leidenalg
polars
pyarrow
tqdm
requests
umap-learn
node2vec
sentence-transformers
ollama
```

Only include packages actually needed by the final notebooks.

## Notebook style rules

Every task section must contain:

1. Task title.
2. Short restatement of the assignment requirement.
3. Explanation of the method.
4. Explanation of why the method was selected.
5. Code.
6. Output/visualization/table.
7. Interpretation of the result.
8. A subsection titled exactly: `How I solved this task`.
9. Limitations, assumptions, or sampling choices where relevant.

Use plain, student-readable explanations. Avoid sounding like a generic LLM-generated report. Be specific about the actual data, code, parameters, and results.

## Execution rules

- Execute notebooks using the project venv kernel.
- Prefer incremental execution while developing.
- Avoid recomputing expensive graph operations repeatedly.
- Cache processed data under `data/processed/` when useful.
- Cache figures under `exports/figures/`.
- Keep notebook outputs visible for grading.
- If an operation is too expensive, sample or filter the graph, explain why, and document the exact sampling method.

## Dataset rules

Raw datasets must be manually placed under `data/raw/` by the student.

Never commit raw datasets.

For every dataset used, document:

- Dataset name.
- Source URL or citation.
- Local expected path.
- File names actually used.
- Schema/columns detected.
- Any filtering or preprocessing.

If a dataset is missing, stop and print exact instructions explaining where it should be placed.

## Large graph safety rules

Never load the full Free Internet Chess Server network into NetworkX. It is too large.

For large graphs:

- Prefer Polars, igraph, or chunked processing.
- Use sampling/filtering when needed.
- Explain the sampling/filtering method in the notebook.
- Never attempt all-pairs shortest paths on large graphs.
- Never compute exact betweenness centrality on huge graphs unless using a justified approximation or sampled subgraph.

## Cytoscape and Gephi rules

Some visualization tasks require Cytoscape and Gephi screenshots.

You may export `.graphml`, `.gexf`, `.csv`, or edge-list files for these tools. You may also write clear manual instructions for the student.

Do not pretend GUI screenshots were created if they were not. Create placeholder markdown cells such as:

```markdown
### Screenshot placeholder: Gephi visualization
TODO: Insert screenshot after opening `exports/gephi/<file>.gexf` in Gephi.
```

## Local LLM rules for Part C

Part C requires a local LLM. Use only a local model such as Ollama, LM Studio, llama.cpp, or a local Hugging Face model.

Default recommendation: Ollama with `qwen2.5:7b-instruct`, unless the student selected another model in `docs/part_c_instructions.md`.

Do not send Enron email text to external web APIs.

Email text should be sampled and truncated before being passed to the local LLM. Explain:

- How users were selected.
- How emails were selected.
- How many emails per user were used.
- Truncation length.
- Prompt used.
- LLM output.
- Whether the student agrees with the classification.

## Git workflow

Use branches:

- `part-a`
- `part-b`
- `part-c`
- `optional-practice`

or more specific sub-branches if needed.

Before starting work:

```bash
git status
```

If the repo is not initialized:

```bash
git init
git add AGENTS.md docs prompts README.md requirements.txt .gitignore
git commit -m "Initialize assignment repository instructions"
```

For each part:

```bash
git checkout main
git pull --ff-only || true
git checkout -b part-a
```

Commit frequently with messages like:

```text
Add Part A notebook scaffold
Implement movie degree distribution analysis
Add Cytoscape and Gephi exports for Part A
Execute Part A notebook
```

If a GitHub remote exists and authentication works:

```bash
git push -u origin part-a
```

If GitHub CLI exists and is authenticated:

```bash
gh pr create --fill
```

If not, print manual PR instructions.

## Final checks before declaring a part complete

For each part:

- Notebook exists.
- Notebook executes start-to-finish or clearly documents any manual-only sections.
- Outputs are visible.
- Figures are saved.
- External visualization files are exported where needed.
- Dataset paths and sources are documented.
- Every assignment question is answered.
- Every task contains `How I solved this task`.
- Limitations and assumptions are included.
- Git commit was created.
- Branch was pushed if possible.
