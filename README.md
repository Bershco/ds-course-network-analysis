# Network Analysis Assignment

This repository is structured for the course assignment on network analysis, visualization, graph embeddings, link prediction, and Enron manager detection.

## Main deliverables

Executed notebooks:

```text
notebooks/part_a.ipynb
notebooks/part_b.ipynb
notebooks/part_c.ipynb
notebooks/optional_practice.ipynb
```

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip wheel setuptools
python -m pip install -r requirements.txt
python -m ipykernel install --user --name network-assignment --display-name "Python (network-assignment)"
```

## Data

Raw datasets are not committed. Place them under:

```text
data/raw/movie_dynamics/
data/raw/directed_network/
data/raw/enron/
data/raw/chess/
```

Fill `docs/dataset_setup.md` before running Codex.

## Codex workflow

1. Fill the relevant manual selections in `docs/part_*_instructions.md`.
2. Start Codex CLI in the repository root.
3. Send the matching prompt from `prompts/`.
4. Review generated code, notebook outputs, commits, and PR.
