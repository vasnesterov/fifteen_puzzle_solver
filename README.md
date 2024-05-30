# 15-puzzle solver
This repository contains a [15-puzzle](https://en.wikipedia.org/wiki/15_Puzzle) solver implemented in the Wolfram Language. It was created as a project for a Wolfram Language course at MIPT.

The solver uses the [A* algorithm](https://en.wikipedia.org/wiki/A*_search_algorithm). A key element of this algorithm is the heuristic function h(s) that estimates how far the state s is from the goal. If h(s) never exceeds the actual distance from s to the goal, the algorithm finds the optimal solution. For the 15-puzzle, a common heuristic is the sum of the Manhattan distances of each tile to its destination. This heuristic guarantees an optimal solution, but in our experiments, it did not always find a solution within a reasonable time frame.

To address this, we use a modified heuristic function: a weighted sum of the Manhattan distances, where the weight of each term corresponds to the number of the tile. With this heuristic, the algorithm consistently finds a (sub-optimal) solution starting from an "average" case.

However, "hard" states, which are far from the goal, remain unsolvable within a reasonable time. To work around this, if the A* algorithm takes too long, we perform some random moves to bring the state to an "average" position and then run the A* algorithm again.

![](https://github.com/vasnesterov/fifteen_puzzle_solver/blob/main/example.gif)
