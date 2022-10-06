# mt_hw3_decoding

We tried three different algorims to find the most probable English translations with log probabilities( in A star search we use -log probablities instead)

In addition, we also updated the `model.py` file for a star search

1. `a greedy search` with prune of stack size (default=100)
2. `a beam-search decoder` with reordering limit (default=5) and distance punishment $log\alpha^{d_{start}-d_{end}-1}$
3. `A* search` with prune 

we remove from this list all words whose inverse translation probability is lower than 0.01 times the best inverse translation probability. This observation pruning is the only pruning involved in our A* search algorithm

- the heuristic function is $H^x(n)=\prod_{j \notin C(n)}h^x(j)$
- takes into account only the translation probability $h^T(j)=max_e p(f_i|e)$



These commands work in a pipeline. For example:

> python decode | python compute-model-score
