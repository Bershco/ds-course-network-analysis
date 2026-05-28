# Part A Instructions — Movie / Social Network Analysis and Optional Network Practice

Before Codex starts Part A, the student must fill the manual selections below.

## Manual selections

```text
==============================
MANUAL_SELECTION_REQUIRED
==============================

SELECTED_MOVIE_OR_SHOW_FOR_A1_A5 = 2013_The_Wolf_of_Wall_Street

WHY_THIS_MOVIE_OR_SHOW_WAS_SELECTED = I selected The Wolf of Wall Street because it is a recognizable movie with a medium-sized character interaction network. The graph is large enough to support meaningful degree distribution, PageRank, triangle, shortest-path, and ego-network analysis, while still being small enough for clear visualization in NetworkX, Cytoscape, and Gephi.

GRAPH_EMBEDDING_METHOD_FOR_A1_2 = Basic graph-level feature vectors + PCA

WHY_THIS_EMBEDDING_METHOD_WAS_SELECTED = I selected basic graph-level feature vectors with PCA because this method is transparent, reproducible, and easy to explain. Instead of relying on a complex embedding model, each movie network is represented using interpretable structural features such as number of nodes, number of edges, density, clustering coefficient, and degree statistics. PCA is then used to project these feature vectors into 2D for visualization. This makes it easier to explain what the embedding captures and what it may miss.

CENTRALITY_METHOD_FOR_A2_TOP_12 = PageRank

WHY_THIS_CENTRALITY_METHOD_WAS_SELECTED = I selected PageRank because it measures not only how many connections a character has, but also how important their neighboring characters are. This is suitable for a movie character interaction network because central characters may be important both through direct interactions and through connections to other influential characters.

SELECTED_VERTEX_FOR_A5_EGO_NETWORK = Jordan Belfort

WHY_THIS_VERTEX_WAS_SELECTED = I selected Jordan Belfort because he is the main character of The Wolf of Wall Street and is expected to be one of the most central vertices in the character interaction network. His ego network should reveal which characters are most directly connected to him and how his local neighborhood reflects his role in the story. If the exact node label is different in the dataset, inspect the graph node labels and use the closest matching Jordan Belfort / Jordan character node.

CHESS_SAMPLING_OR_FILTERING_STRATEGY_FOR_A6 = Process the FICS chess edge list using streaming or chunked reading from the compressed archive. Do not load the full graph into NetworkX. First compute an approximate or exact interaction count / degree-like score for players using Polars, pandas chunking, or another memory-safe method. Then identify the top central players according to this score and create a visualization subgraph containing the top players and a limited number of their neighbors.

WHY_THIS_STRATEGY_IS_REASONABLE = This strategy is reasonable because the FICS network is too large to load directly into memory with standard NetworkX methods. The assignment explicitly allows sampling or meaningful subgraph analysis for large networks. Counting player interactions from the edge list gives a scalable approximation of centrality, and visualizing the neighborhood around the most central players creates an interpretable subgraph without exhausting system memory.

LOTR_COUPLES_DATA_PATH_FOR_A7 = data/raw/lotr_couples/lotr_characters.csv

GENDER_ATTRIBUTE_COLUMN_OR_MAPPING = gender

RACE_ATTRIBUTE_COLUMN_OR_MAPPING = race

==============================
END_MANUAL_SELECTION_REQUIRED
==============================
```

## Tasks to implement

Create and execute:

```text
notebooks/part_a.ipynb
```

This notebook must cover:

- A1.1 Degree distribution for one selected movie/show network.
- A1.2 Graph embeddings for multiple movie/show networks.
- A2 Top-12 character subgraph using one centrality algorithm.
- A3 PageRank, triangles, and average shortest paths.
- A4 Cytoscape and Gephi exports plus screenshot placeholders/instructions.
- A5 Ego network function.
- A6 Large chess network analysis.
- A7 Lord of the Rings Couples Cytoscape export and screenshot placeholder.

## A1.1 Degree distribution

Requirements:

- Load the selected movie/show graph.
- Calculate degree of each vertex.
- Plot degree distribution.
- Explain what the distribution says about the network.

The explanation should mention whether the network appears centralized around a few characters or more evenly distributed.

## A1.2 Graph embeddings of movie networks

Requirements:

- Load multiple movie/show networks.
- Create one vector per graph.
- Use the selected embedding method.
- Reduce to 2D using PCA, t-SNE, UMAP, or another explained method.
- Visualize graphs as points.
- Identify interesting clusters/pairs.
- Explain what the embedding captures and misses.

If the selected method is basic graph-level features, include features such as:

- Number of nodes.
- Number of edges.
- Density.
- Average clustering coefficient.
- Degree mean/std/max.
- Connected component statistics.

## A2 Top-12 character subgraph

Requirements:

- Use the selected centrality algorithm.
- Rank characters.
- Select top 12.
- Create induced subgraph.
- Draw circular layout.
- Explain why the centrality method was selected.

## A3 PageRank, triangles, shortest paths

Requirements:

For every vertex in the selected graph, compute:

- PageRank.
- Number of triangles.
- Average shortest path length.

If the graph is directed, clearly decide whether each measure uses directed or undirected conversion and explain why.

Show a DataFrame sorted by interesting values.

## A4 Cytoscape and Gephi

Requirements:

- Export selected network to Cytoscape-compatible and Gephi-compatible formats.
- Vertex size must correlate with degree.
- Include screenshot placeholders.
- Include manual instructions for how to style the graph in Cytoscape and Gephi.

Do not pretend screenshots were created automatically.

## A5 Ego network function

Requirements:

Write a function that receives a selected vertex and creates a subgraph containing:

- The selected vertex.
- All incoming neighbors.
- All outgoing neighbors.

Then:

- Draw the subgraph.
- Calculate number of vertices.
- Calculate number of edges.
- Explain what the ego network reveals about the selected vertex.

If the graph is undirected, explain how incoming/outgoing neighbors are interpreted.

## A6 Large Chess Network

Requirements:

- Use the Free Internet Chess Server network.
- Find top 10 most central players.
- Visualize a meaningful part of the network.
- Explain handling of network size.

Critical safety rule:

Do not load the full chess network into NetworkX.

Use Polars/igraph/chunking/sampling/filtering.

If exact centrality is impossible on the full graph, use a justified approximation and explain it clearly.

## A7 Lord of the Rings Couples network

Requirements:

- Export network to Cytoscape.
- Vertices colored by gender.
- Vertex shapes represent race.
- Include screenshot placeholder.
- Explain visualization design choices.

## Final Part A checks

Before finishing:

- Execute the notebook.
- Save figures.
- Save exported graph files.
- Confirm every task has `How I solved this task`.
- Commit changes.
- Push branch and open PR if possible.
