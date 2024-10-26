# LEETCODE-TREES-2458
### Key Methods and Data Structures

1. **`treeQueries(TreeNode root, int[] queries)`**:
   - This is the main function that calculates the results for each query. For each node in `queries`, it returns the maximum height of the tree if that node were removed.
   - To achieve this, it uses two helper functions:
     - **`dfs(TreeNode root, int depth, int maxHeight)`** - Populates `valToMaxHeight`, mapping each node to the maximum tree height without that node.
     - **`height(TreeNode root)`** - Calculates and caches the height of each node to avoid redundant calculations, storing the results in `valToHeight`.

2. **Data Structures**:
   - **`valToMaxHeight`**: Maps each node's value to the maximum height of the tree if that node were removed.
   - **`valToHeight`**: Maps each node's value to its height in the tree.
  
### Dry Run

Let's go through a hypothetical scenario with the following structure:

```
      1
     / \
    2   3
   / \
  4   5
```

For example, if the queries array is `[1, 2, 3]`, we want the height of the tree without nodes `1`, `2`, and `3`.

1. **First Call to `dfs`**:
   - We start at the root node (`1`), and we will recursively populate `valToMaxHeight` for each node.

2. **Calculation of Heights Using `height`**:
   - For node `1`, calculate its height:
     - Height of node `2` is calculated as `1 + max(height(4), height(5)) = 2`.
     - Height of node `3` is `1`.
     - Thus, `height(1) = 1 + max(2, 1) = 3`.

3. **Populate `valToMaxHeight`**:
   - Starting from the root, `dfs` updates `valToMaxHeight` for each node.
   - For example:
     - For node `1`, `maxHeight` without `1` is `0`.
     - For node `2`, `maxHeight` is `Math.max(0, 1 + height(3)) = 2` without `2`.
     - Similarly, the heights are calculated and stored for nodes `3`, `4`, and `5`.

4. **Answer Construction**:
   - Finally, `treeQueries` retrieves the height without each queried node from `valToMaxHeight` and returns it in the result array `ans`.

### Final Thoughts

This solution leverages depth-first traversal to efficiently calculate heights without redundant computations and relies on memoization in `valToHeight` and `valToMaxHeight` for optimized performance. The result array `ans` will provide the tree heights after each specified node is hypothetically removed.
