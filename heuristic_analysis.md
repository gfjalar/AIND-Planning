# Heuristic Analysis

## Optimal Solutions

### Problem 1

```
Plan length: 6

Load(C1, P1, SFO)
Fly(P1, SFO, JFK)
Load(C2, P2, JFK)
Fly(P2, JFK, SFO)
Unload(C1, P1, JFK)
Unload(C2, P2, SFO)
```

### Problem 2

```
Plan length: 9

Load(C1, P1, SFO)
Fly(P1, SFO, JFK)
Load(C2, P2, JFK)
Fly(P2, JFK, SFO)
Load(C3, P3, ATL)
Fly(P3, ATL, SFO)
Unload(C3, P3, SFO)
Unload(C2, P2, SFO)
Unload(C1, P1, JFK)
```

### Problem 3

```
Plan length: 12

Load(C2, P2, JFK)
Fly(P2, JFK, ORD)
Load(C4, P2, ORD)
Fly(P2, ORD, SFO)
Load(C1, P1, SFO)
Fly(P1, SFO, ATL)
Load(C3, P1, ATL)
Fly(P1, ATL, JFK)
Unload(C4, P2, SFO)
Unload(C3, P1, JFK)
Unload(C2, P2, SFO)
Unload(C1, P1, JFK)
```

## Hardware Setup

Heuristic analysis was performed on a machine with `2.5 GHz Intel Core i5` processor and `16 GB 2133 MHz DDR4` of RAM.

## Performance Testing

### Problem 1

| Search | Expansions | Goal Tests | New nodes | Plan Length | Time Elapsed(s) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| breadth_first_search | 43 | 56 | 180 | **6** | 0.035 |
| depth_first_graph_search | 21 | 22 | 84 | 20 | **0.014** |
| uniform_cost_search | 55 | 57 | 224 | **6** | 0.040 |
| astar_search with h_1 | 55 | 57 | 224 | **6** | 0.025 |
| astar_search with h_ignore_preconditions | 41 | 43 | 170 | **6** | 0.270 |
| astar_search with h_pg_levelsum | **11** | **13** | **50** | **6** | 0.898 |

### Problem 2

| Search | Expansions | Goal Tests | New nodes | Plan Length | Time Elapsed(s) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| breadth_first_search | 3343 | 4609 | 30509 | **9** | 11.110 |
| depth_first_graph_search |  624 | 625 | 5602 | 619 | 3.425 |
| uniform_cost_search | 4852 | 4854 | 44030 | **9** | 9.867 |
| astar_search with h_1 | 4852 | 4854 | 44030 | **9** | 4.795 |
| astar_search with h_ignore_preconditions | 1450 | 1452 | 13303 | **9** | **1.584** |
| astar_search with h_pg_levelsum | **86** | **88** | **841** | **9** | 74.427 |

### Problem 3

| Search | Expansions | Goal Tests | New nodes | Plan Length | Time Elapsed(s) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| breadth_first_search | 14663 | 18098 | 129631 | **12** | 98.740 |
| depth_first_graph_search | 408 | 409 | 3364 | 392 | **1.353** |
| uniform_cost_search | 18235 | 18237 | 159716 | **12** | 25.591 |
| astar_search with h_1 | 18235 | 18237 | 159716 | **12** | 25.502 |
| astar_search with h_ignore_preconditions | 5040 | 5042 | 44944 | **12** | 7.031 |
| astar_search with h_pg_levelsum | **315** | **317** | **2902** | **12** | 305.456 |

## Non-heuristic Searches Comparison

### Optimality of the Solution

Only the depth first graph search did not find the optimal solution in any of the problems. This is due to the fact that the depth first graph search strategy aims to explore a given path to the solution as long as there exists an extension to it. All the other tested search strategies come up with optimal results.

### Time Elapsed

Even though the depth first graph search strategy is not optimal, it does bring a significant time advantage to the table. It is the fastest strategy used across all three problems.

### Node Expansions

In terms of node expansions the depth first graph search strategy is the best again with significantly fewer nodes expanded than in other strategies.

### Summary

The depth first graph search strategy is by far the fastest and expands few nodes. It might be a fairly good choice for problems where one does not care for the optimal solution and where there are many valid solutions so that the search does not expand to many invalid branches. However, when those criteria are not met, one should take a look at the breadth first search and uniform cost search. They both always find the optimal solutions. Additionally, the first one does a pretty good job when it comes to the node expansion while the latter outperforms the first one in terms of time complexity as the problem space grows.

## Heuristic Searches Comparison

### Optimality of the Solution

All the A\* searches used in the tests always find the best possible solution if one exists. They are all optimal.

### Time Elapsed

The fastest A\* search was performed with the use of ignore preconditions heuristic. This is due to its' small computational complexity.

### Node Expansions

In terms of node expansions the A\* search with levelsum heuristic is the winner across all three problems. It expands the least nodes by far. This is because it carefully plans which nodes to expand.

### Summary

In terms of node expansion the A\* search with levelsum heuristic does the best job overall, however it leaves a significant mark on time performance as the heuristic is computationally expensive and requires additional planning graph to work. A\* search with ignore preconditions heuristic seems to be a good compromise between the number of nodes expanded by the search and the time it requires to find an optimal solution.

## Summary

Overall, the A\* search with levelsum heuristic expands the least nodes out of the tested searches regardless of the problem it faces. This is due to the fact it plans which nodes to expand using a planning graph. As a result, this search becomes computationally expensive to performs which shows in the times it needs to find the optimal solution. To improve the time complexity, a depth first graph search may be used. However, it does not always find the optimal solution so the use case for this search strategy is limited. As a compromise between the two, a search strategy like A\* search with ignore preconditions heuristic could be chosen. As it performs really well in terms of time complexity, expands relatively few nodes and at the same time the heuristic it uses is not computationally expensive. Additionally, it is a great showcase for the difference between the informed and uninformed searches[1].

# References

0. Stuart J. Russell, Peter Norvig (2003). ["Artificial Intelligence: A Modern Approach"](http://aima.cs.berkeley.edu/)
