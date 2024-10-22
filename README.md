# PageRank Algorithm Implementation

This repository contains multiple implementations of the **PageRank algorithm**, a link analysis algorithm used to determine the importance of nodes in a graph. The project showcases three different methods to compute PageRank using Python, and it also demonstrates how to use the built-in PageRank function from the `NetworkX` library. 

---

## Table of Contents
1. [Introduction](#introduction)
2. [Project Structure](#project-structure)
3. [Usage](#usage)
4. [Methods](#methods)
   - Method 1: Adjacency Matrix
   - Method 2: XML Graph
   - Method 3: Graph Edges List
   - Built-in `NetworkX` Method
5. [Example Output](#example-output)
6. [Dependencies](#dependencies)

---

## Introduction
The **PageRank algorithm** evaluates the relative importance of nodes in a graph by simulating the behavior of a random web surfer. It was originally developed by Google to rank web pages. 

This project provides:
- A **core implementation** of the PageRank algorithm.
- **Multiple ways to input graphs**: using an adjacency matrix, XML files, or manually defined edges.
- **Comparison with NetworkX’s built-in PageRank** functionality.

---

## Project Structure
- **`page_rank_score()`**: Core algorithm to compute PageRank.
- **Method 1**: Using an **adjacency matrix**.
- **Method 2**: Using an **XML** graph structure.
- **Method 3**: Using **manually defined edges**.
- **Built-in NetworkX** implementation for comparison.

---

## Usage

1. **Clone the repository**:
   ```bash
   git clone https://github.com/safaeOulaja/PageRank-Algorithm-Implementation.git
   cd PageRank-Algorithm-Implementation
   ```

2. **Run the code**:
   ```bash
   python Project-PageRank.py
   ```

3. **Modify inputs**: Use different graphs (e.g., XML files or adjacency matrices) by updating the code sections.

---

## Methods

### Method 1: PageRank from Adjacency Matrix
Use an **adjacency matrix** to represent the graph structure. Each row indicates outgoing links from a node.

```python
adj_matrix = np.array([
    [0, 0, 0, 0, 0],  # Node A
    [0, 0, 1, 0, 0],  # Node B -> C
    [1, 1, 0, 0, 0],  # Node C -> A, B
])
page_ranks = page_rank_score_method1(adj_matrix)
```

---

### Method 2: PageRank from XML Graph
Parse an XML file containing nodes and edges to construct the graph.

```python
page_ranks, node_map = page_rank_score_method2('graph.xml')
```

**Example XML structure:**
```xml
<graph>
  <node id="A">
    <edge target="B" />
  </node>
  <node id="B">
    <edge target="C" />
  </node>
</graph>
```

---

### Method 3: PageRank from Graph Edges List
Define the graph with **nodes and edges** directly in the code.

```python
nodes = ['A', 'B', 'C']
edges = [('A', 'B'), ('B', 'C'), ('C', 'A')]
page_ranks, node_map = page_rank_score_method3(nodes, edges)
```

---

### Built-in NetworkX Method
Use **`NetworkX`** to directly compute PageRank.

```python
import networkx as nx

graph = {'A': ['B'], 'B': ['C'], 'C': ['A']}
G = nx.DiGraph(graph)
page_ranks = nx.pagerank(G, alpha=0.85)
```

---

## Example Output

```
PageRank from Adjacency Matrix:
Converged in 81 iterations.
The PageRank of node A: 3.3%
The PageRank of node B: 38.4%
The PageRank of node C: 34.3%

PageRank from XML:
Converged in 81 iterations.
The PageRank of node B: 38.4%
The PageRank of node C: 34.3%

PageRank using NetworkX:
The PageRank of node A: 3.3%
The PageRank of node B: 38.4%
```

---

## Dependencies

Make sure to install the required libraries:

```bash
pip install numpy networkx
```

---

## Contributing
Feel free to submit pull requests or issues if you find any bugs or want to suggest improvements.
