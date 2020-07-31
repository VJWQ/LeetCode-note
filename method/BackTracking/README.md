## Backtracking and DFS:

Backtracking is usually implemented as DFS plus search pruning. So in reality as you do DFS, you need to also prune partial solutions, which do not make sense in context of the actual task, and focus on the partial solutions, which can lead to valid optimal solutions. This is the actual backtracking technique - you discard partial solutions as early as possible, make a step back and try to find local optimum again.   
Backtracking handles an implicit tree and DFS deals with an explicit one. When the search space of a problem is visited by backtracking, the implicit tree gets traversed and pruned in the middle of it. Yet for DFS, the tree/graph it deals with is explicitly constructed and unacceptable cases have already been thrown, i.e. pruned, away before any search is done.  
Usually, a depth-first-search is a way of iterating through an actual graph/tree structure looking for a value, whereas backtracking is iterating through a problem space looking for a solution. Backtracking is a more general algorithm that doesn't necessarily even relate to trees.   
I would say, DFS is the special form of backtracking; backtracking is the general form of DFS.

If we extend DFS to general problems, we can call it backtracking. If we use backtracking to tree/graph related problems, we can call it DFS.

They carry the same idea in algorithmic aspect.  

DFS可以使用非递归来实现；使用递归函数的时候，我们使用的是操作系统中的栈，所以不需要手动建立栈；DFS和BFS的搜索顺序是截然不同的，除非是在一条链上搜索。   

回溯是一种通用的算法，把问题分步解决，在每一步都试验所有的可能，当发现已经找到一种方式或者目前这种方式不可能是结果的时候，退回上一步继续尝试其他可能。很多时候每一步的处理都是一致的，这时候用递归来实现就很自然。  

当回溯用于树的时候，就是深度优先搜索（related problems could be found under the category of DFS）。当然了，几乎所有可以用回溯解决的问题都可以表示为树。那么这俩在这里就几乎同义了。如果一个问题解决的时候显式地使用了树，那么我们就叫它dfs。很多时候没有用树我们也管它叫dfs严格地说是不对的，但是dfs比回溯打字的时候好输入。别的回答里提到了砍枝，实际上这二者都可以砍枝。






