# Discrete L(2,1) Graph Coloring Final 
- [Installing Requirements](#installing-requirements)

  - [requirements.txt install](#requirements-txt-install)

  - [conda install](#conda-install)

- [What is L(2,1)](#what-is-l21)

## Installing Requirements 

We offer a `requirements.txt` for traditional pip install or a conda
`environment.yml` file. Note that Quarto is required to run the `.qmd` file.

### requirements.txt install

To install the requirements using `pip`, run the following code:

```bash
pip install -r requirements.txt
```

Note that this assumes that you already have Python installed on your system.

### conda install

To create a conda environment with the necessary requirements, run the following
code:

```bash
conda env create -f environment.yml
```

Note that this assumes that you have Anaconda or Miniconda setup on your system.

## What is L(2,1)

L(2,1) is a method of graph vertex labeling. For a graph, whenever x and y are
two adjacent vertices then their label must have a distance greater than or
equal to two. Whenever x and y are two vertices with distance **two** between
them, then their label must have a distance greater than or equal to **one**.
There are many ways to weigh how well an L(2,1) labeling algorithm performs but
two main ones are to minimize the number of labels used or to minimize the
number of holes in a labeled graph. A hole is when a vertex label is never used
(i.e. it is skipped over to maintain the L(2,1) rule). Our code implements two
approaches to L(2,1) labeling: greedy and Chang Kuo.

### What is Greedy Labeling?

Greedy labeling works by going vertex to vertex and assigning the lowest
possible label (e.g. 0). But, to not break the rules of L(2,1) labeling, it
looks at any vertex distance one from itself and makes sure that the new label
is at least two different from all of the adjacent vertexes. It does the same
for any vertexes distance two, ensuring that the new label is at least one
different from any of them. If the label to be placed violates any of these
checks, then it is increased by one and the process starts again until every
vertex has a label. However, this approach has many flaws as it often uses too
many labels, in addition to being prone to many holes.

### What is Chang Kuo Labeling?

Change Kuo labeling fundamentally differs in that it looks at all vertexes at a
time when assigning labels. It's goal to assign the lowest label to as many of
the vertexes as L(2,1) will allow before moving on to the next label. Of course,
it will still follow the distance limitations of the greedy algorithm. This
approach usually uses less labels and has less holes.
