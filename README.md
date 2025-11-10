# Recursive Spectral Modularity Partitioning of Zachary's Karate Club
__Done by: Jibin Chalissery__

__Roll no: IMS24112__

This repository contains a complete, runnable Jupyter Notebook that fulfills all tasks for the DSC212 Graph Theory project. The notebook implements the recursive spectral modularity algorithm from scratch to find and analyze the community structure of the famous Zachary's Karate Club graph.
# Project Overview
The Zachary's Karate Club graph is a classic dataset in network science, documenting the friendships between 34 members of a university karate club in the 1970s. The dataset is famous because a real-life conflict between the club's instructor (Node 0, "Mr. Hi") and its administrator (Node 33, "John A.") caused the club to split into two new factions.   

This project uses the friendship data (collected before the split) to answer a key question: Can a mathematical algorithm, looking only at the graph's structure, predict the "social fault lines" that led to this real-world split?.
# Tasks Completed
The submitted notebook (FINAL_DSC.ipynb) successfully completes all required tasks:
- [x] Task 1: Implemented the recursive spectral modularity partitioning algorithm from scratch, using the leading eigenvector of the restricted modularity matrix for bisection and the eigenvalue stopping criterion ($\lambda_1 \le 0$).
- [x] Task 2: Visualized the graph after each iterative split, using a fixed layout and unique coloring to show the partitioning process.
- [x] Task 3: Computed the four required node metrics (Degree Centrality, Betweenness Centrality, Closeness Centrality, and Clustering) after each split.
- [x] Task 4: Plotted the evolution of these metrics across all iterations.
- [x] Task 5: Wrote a detailed discussion synthesizing all findings and analyzing the relationship between node centrality and community structure.
- [x] Advanced Step: Added a post-processing cell to clean up the partition by reassigning "singleton" (single-node) communities, improving the final modularity score.
- [x] Advanced Step: Added a final summary cell to quantify the results, including final community membership, modularity score, and top nodes per community.
# Methodology: The Analytical Approach to Plotting
A key part of this assignment is Task 4, plotting the evolution of node metrics, which directly informs the discussion for Task 5.

__The Problem with a Naive Plot__

The assignment asks to plot the metrics for every node. A naive plot of all 34 nodes is unreadable. It produces a "spaghetti graph" of overlapping lines, making it impossible to identify which nodes are the important ones.

__The Solution: Enhanced "Leaders vs. Members" Plots__

To solve this and directly answer Task 5 ("which nodes consistently remain central?") , this project uses a more insightful visualization strategy in Cell 6.   

The analysis is based on a clear hypothesis: the network's structure is not democratic; it is dominated by the two main actors, Node 0 and Node 33.   

Therefore, the plots were designed to test this hypothesis directly:

1. Isolate Leaders: We explicitly highlight the two leaders, "Node 0 (Mr. Hi)" and "Node 33 (John A.)".
2. Average the Rest: We group all other 32 members into a single 'Other Members' category.
3. Compare: The seaborn.lineplot function then automatically plots the two leaders as individual lines and contrasts them against the statistical mean of the "Other Members" group.

This enhanced plotting strategy (visible in Cell 6) creates clear, legible graphs with a simple legend. It allows us to immediately see that Nodes 0 and 33 are massive outliers in key centrality measures, providing a clear "smoking gun" for the final analysis.

# Key Findings
__1. Centrality Predicts the Split__: The plots show that Nodes 0 and 33 are the most central nodes by Degree, Betweenness, and Closeness. The algorithm's first and most significant split correctly partitions the graph into two factions anchored by these two leaders.   

__2. Leaders are "Brokers," Not "Clique Members"__: A key insight comes from the Clustering Coefficient plot. Nodes 0 and 33 have a lower clustering score than the average member. This indicates their role as brokers (high betweenness, connecting many disparate groups) rather than as members of a tight-knit "clique" (which would have high clustering).
