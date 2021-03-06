# evolvingrl
Supplementary Data for [Evolving Reinforcement Learning Algorithms ](https://arxiv.org/abs/2101.03958)

This dataset contains 1000 loss graphs from two experiments: 500 unique graphs
learned from scratch, and 500 unique graphs seeded by the DQN loss.

There are two csv files: from_scratch.csv and dqn_seeded.csv. They have two
columns: id and reward. Each file is sorted by reward from highest to lowest.
Graph with <id> is visualized in a png file named <id>.png. These graphs are
under folders from_scratch_graphs/ and dqn_seeded_graphs/.

Notes on reading the graph:
- Input nodes are in green, the output node is in blue.
- The directed edges represent the data flow. A red edge represents the 2nd
  input for a binary operator, and all other edges are in black. Such coloring
  scheme is necesssary for encoding inputs for non-commutative operators like
  -, /, etc.
- It’s common to have isolated input nodes and intermediate nodes that do not
  contribute to the final output. We can ignore these nodes.
- As an example, Q(s_{t-1}, a_{t-1}) is represented by 5 nodes:
  * Q_param → QValueListOp ← s_tm1. This gives Q(s_{t-1}, -).
  * QValueListOp → SelectList ← a_{t-1}. This uses a_{t-1} to index into
    Q(s_{t-1}, -).
