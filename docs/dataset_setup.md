# Dataset Setup

Codex must not waste time searching randomly for datasets. The student should manually download datasets once and place them under `data/raw/`.

## Required local folder layout

```text
data/raw/
├── movie_dynamics/
├── directed_network/
├── enron/
└── chess/
```

## Dataset inventory table

Fill this table before running Codex on the relevant part.

| Part | Dataset | Source URL | Local folder | Exact files expected | Notes |
|---|---|---|---|---|---|
| A | Movie Dynamics Networks | MANUAL_SELECTION_REQUIRED: ADD_URL_HERE | `data/raw/movie_dynamics/` | MANUAL_SELECTION_REQUIRED: ADD_FILE_NAMES | Required for A1-A5 |
| A6 | Free Internet Chess Server network | MANUAL_SELECTION_REQUIRED: ADD_URL_HERE | `data/raw/chess/` | MANUAL_SELECTION_REQUIRED: ADD_FILE_NAMES | Very large; never load fully into NetworkX |
| A7 | Lord of the Rings Couples network | MANUAL_SELECTION_REQUIRED: ADD_URL_HERE_OR_LECTURE_FILE | `data/raw/movie_dynamics/` or another documented path | MANUAL_SELECTION_REQUIRED: ADD_FILE_NAMES | Used for Cytoscape visualization |
| B | Directed network | MANUAL_SELECTION_REQUIRED: ADD_SELECTED_DATASET_AND_URL | `data/raw/directed_network/` | MANUAL_SELECTION_REQUIRED: ADD_FILE_NAMES | Used for directed link prediction |
| C | Enron email network | MANUAL_SELECTION_REQUIRED: ADD_URL_HERE | `data/raw/enron/` | MANUAL_SELECTION_REQUIRED: ADD_FILE_NAMES | Need graph data and email content if available |

## Codex behavior if files are missing

If files are missing, Codex must stop and print:

1. Which file/folder is missing.
2. Which task needs it.
3. Where the file should be placed.
4. Which URL/source was specified by the student.
5. No invented fallback dataset unless explicitly approved in the instruction file.

## Reproducibility requirements

Each notebook must include a dataset description cell with:

- Dataset name.
- Source URL.
- Local path.
- File names used.
- Loading code.
- Detected schema/columns.
- Any preprocessing, filtering, or sampling.

## Do not commit datasets

Raw datasets and processed datasets should not be committed.

Use `.gitignore` to exclude:

```text
data/raw/
data/processed/
*.csv
*.tsv
*.parquet
*.feather
*.gexf
*.graphml
*.gpickle
*.pickle
*.pkl
```

Exception: small manually created metadata files may be committed if useful.
