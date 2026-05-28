# Part C Instructions — Enron Manager Detection and Local LLM Analysis

Before Codex starts Part C, the student must fill the manual selections below.

## Manual selections

```text
==============================
MANUAL_SELECTION_REQUIRED
==============================

ENRON_GRAPH_FILE_PATH = data/raw/enron/email-Enron.txt.gz

ENRON_EMAIL_CONTENT_PATH = data/raw/enron/enron_mail_20150507.tar.gz

ENRON_MANAGER_LABELS_PATH_IF_AVAILABLE = NONE

ENRON_DATASET_SOURCE_URL = https://snap.stanford.edu/data/email-Enron.html

CENTRALITY_ALGORITHM_1 = PageRank

CENTRALITY_ALGORITHM_2 = Betweenness Centrality

CENTRALITY_ALGORITHM_3 = HITS Authority Score

LOCAL_LLM_TOOL = Ollama

LOCAL_LLM_MODEL = qwen2.5:7b-instruct

NUMBER_OF_USERS_TO_ANALYZE_WITH_LLM = 10

NUMBER_OF_EMAILS_PER_USER_FOR_LLM = 15

MAX_CHARACTERS_PER_EMAIL_FOR_LLM = 4000

EMAIL_SELECTION_STRATEGY_FOR_LLM = Sample representative sent and received emails for each selected user based on communication frequency while truncating long email bodies to reduce local LLM context size.

VISUALIZATION_CENTRALITY_MEASURE = PageRank

ENRON_SUBGRAPH_SAMPLING_STRATEGY_FOR_VISUALIZATION = Create a meaningful subgraph containing the top-ranked users according to PageRank together with their strongest communication neighbors in order to keep the visualization readable and interpretable.

==============================
END_MANUAL_SELECTION_REQUIRED
==============================
```

## Task to implement

Create and execute:

```text
notebooks/part_c.ipynb
```

The notebook must cover manager detection using:

- network centrality;
- local LLM classification from email evidence;
- local LLM role summarization;
- visualization;
- discussion.

## C1.1 Network and label description

Include:

- Description of Enron email network.
- What nodes represent.
- What edges represent.
- Whether graph is directed/weighted.
- Available manager labels, if any.
- Preprocessing performed.

## C1.2 Centrality-based manager detection

Use exactly three centrality algorithms selected by the student.

For each algorithm:

- Compute centrality.
- Rank nodes.
- Show top 10.
- If labels exist, compute precision@10:

```text
precision@10 = number of true managers in top 10 / 10
```

Compare the algorithms.

If labels are unavailable, clearly say precision@10 cannot be computed and explain the alternative evidence used.

## C1.3 Local LLM-based manager identification

Use only a local LLM.

Default: Ollama with `qwen2.5:7b-instruct`.

Before calling the LLM:

- Verify Ollama is installed.
- Verify the model exists.
- If missing, stop and print setup commands.

Do not use external LLM APIs.

For likely manager candidates:

- Select users from centrality results.
- Sample emails written by or sent to the user.
- Truncate emails.
- Build a structured prompt.
- Ask the model whether the user appears to be a manager.
- Store raw model response in the notebook output or a local cache.
- Parse classification if possible.

The notebook must include the exact prompt used.

## Required local LLM prompt template

Use or adapt this prompt:

```text
You are analyzing historical Enron email evidence locally. Do not use outside knowledge.

Task: Decide whether the email user appears to be a manager or non-manager based only on the email evidence below.

User identifier: {user_id}

Evidence emails:
{email_snippets}

Return a compact structured answer:
- classification: manager / non-manager / uncertain
- confidence: low / medium / high
- reasoning: 3-5 bullet points grounded only in the emails
- evidence: quote or summarize 2-3 short email-based signals
```

## C1.4 Summarizing manager roles with a local LLM

For users identified as likely managers:

- Ask the local LLM to summarize likely role.
- Base summary only on email evidence.
- Include 2-3 examples of evidence.
- Include uncertainty.

## C1.5 Network visualization

Create a visualization of the Enron network or a meaningful subgraph.

Requirements:

- Node size based on selected centrality.
- Clear layout.
- Highlight likely managers.
- Explain subgraph sampling.

## C1.6 Discussion

Discuss:

- Managers identified by centrality.
- Managers identified by local LLM.
- Managers in labels, if available.
- Which method worked best.
- Disagreements.
- Possible mistakes.
- Limitations of email content and LLM role detection.

## Final Part C checks

Before finishing:

- Execute the notebook.
- Confirm all local LLM outputs are visible or cached.
- Confirm no external LLM API was used.
- Confirm every task has `How I solved this task`.
- Commit changes.
- Push branch and open PR if possible.
