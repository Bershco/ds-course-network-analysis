# Part B Instructions — Directed Link Prediction

Before Codex starts Part B, the student must fill the manual selections below.

## Manual selections

```text
==============================
MANUAL_SELECTION_REQUIRED
==============================

SELECTED_DIRECTED_NETWORK_NAME = Bitcoin Network

SELECTED_DIRECTED_NETWORK_SOURCE_URL = https://dynamics.cs.washington.edu/data.html

LOCAL_DIRECTED_NETWORK_FILE_PATH = data/raw/directed_network/bitcoin.tar.gz

WHY_THIS_DIRECTED_NETWORK_WAS_SELECTED = I selected the Bitcoin network because it is a real-world directed transaction network with meaningful interaction structure. The dataset is large enough to support meaningful link prediction experiments while still being manageable within the assignment constraints.

POSITIVE_EDGE_DEFINITION = Existing directed edges (u,v) that appear in the observed graph.

NEGATIVE_EDGE_SAMPLING_STRATEGY = Randomly sample node pairs (u,v) that do not have an existing directed edge while avoiding duplicate samples and self-loops.

TRAIN_TEST_SPLIT_STRATEGY = Use a standard random edge split for the main experiments, and additionally perform a temporal train/test split for the bonus future-link prediction task if timestamp information is available in the dataset.

BASELINE_CLASSIFIER_CHOICE = Directed topology features with Logistic Regression

IMPROVED_CLASSIFIER_CHOICE = Random Forest using graph embedding features

NODE_OR_LINK_EMBEDDING_METHOD = Node2Vec embeddings combined into link features

EVALUATION_METRICS_TO_REPORT = AUC, Accuracy, Precision, Recall, F1

DO_BONUS_FUTURE_LINK_PREDICTION = YES

TIMESTAMP_COLUMN_IF_BONUS_IS_USED = INSPECT_DATASET_AND_USE_AVAILABLE_TIMESTAMP_FIELD_IF_PRESENT

==============================
END_MANUAL_SELECTION_REQUIRED
==============================
```

## Task to implement

Create and execute:

```text
notebooks/part_b.ipynb
```

The notebook must implement a directed link prediction classifier using the selected directed network.

## Required sections

### 1. Dataset description

Include:

- Name of directed network.
- Source.
- Local file path.
- What nodes represent.
- What directed edges represent.
- Number of nodes and edges.
- Whether timestamps exist.

### 2. Positive and negative examples

Positive examples are real directed edges.

Negative examples should be sampled from node pairs where the directed edge does not exist.

Explain:

- How many negatives were sampled.
- Whether class balancing was used.
- How impossible/self edges were avoided.
- Whether reverse edges are treated as different examples.

### 3. Train/test split

Implement the selected split strategy.

If random split:

- Use fixed random seed.
- Avoid leakage where possible.

If temporal split:

- Sort by timestamp.
- Train on earlier edges.
- Test on later edges.

### 4. Baseline classifier

Implement a simple topology-based baseline.

Possible features:

- Source out-degree.
- Source in-degree.
- Target out-degree.
- Target in-degree.
- Common successors.
- Common predecessors.
- Directed Jaccard.
- Preferential attachment using source out-degree and target in-degree.

Use a simple model such as logistic regression, decision tree, or random forest, depending on the manual selection.

### 5. Improved classifier

Use node embeddings or link embedding features.

Possible options:

- Node2Vec on directed or symmetrized graph, with explanation.
- Spectral embeddings.
- Graph-level/node-level embedding features.
- Concatenation, Hadamard product, absolute difference, or average of source/target embeddings.

Explain exactly how edge features are constructed.

### 6. Evaluation

Report selected metrics, such as:

- AUC.
- Accuracy.
- Precision.
- Recall.
- F1.
- Confusion matrix.

Compare baseline and improved model.

### 7. Bonus: future link prediction

Only do this if `DO_BONUS_FUTURE_LINK_PREDICTION = YES` and timestamps exist.

Requirements:

- Temporal train/test split.
- Compare random link prediction vs future link prediction.
- Discuss whether the classifier generalizes to future links.

## Final Part B checks

Before finishing:

- Execute the notebook.
- Save figures/tables.
- Confirm every required item is answered.
- Include `How I solved this task`.
- Commit changes.
- Push branch and open PR if possible.
