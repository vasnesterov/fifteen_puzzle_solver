# 15-puzzle solver
This repo contains a 15-puzzle solver implemented in Wolfram Language. This is done as project for a Wolfram Language course at MIPT. 

The solver uses the A* algorithm. The key element of this algorithm is the heuristic function h(s) that estimates how far is the state s from the goal. If h(s) never exceeds the distance between s and the goal, the algorithm finds the optimal solution. In the case of 15-puzzle the obvious option is to use the sum of Manhattan distances from each tile to its destination as h(s). This option guarantees the optimality of the solution, but in out experiments not always found (any) solution in reasonable time. Here we use the modification of described function: we use weighted sum of Manhattan distances and weight of each term is equal to the number of tile. With this h(s) the algorithm always finds the (sub-optimal) solution starting from some "average" case.

"Hard" states, which are far from the goal, are still cannot be solved. To work around this problem, we use the following trick: if the A* algorithm takes too much time we do some random moves (making our state "average") and then run the A*.
