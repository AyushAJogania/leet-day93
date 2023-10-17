# leet-day93

# Validate Binary Tree Nodes - LeetCode

## Problem Description

You are given `n` binary tree nodes numbered from 0 to `n - 1`, where node `i` has two children `leftChild[i]` and `rightChild[i]`. Your task is to determine if these nodes form exactly one valid binary tree.

- A valid binary tree satisfies the following conditions:
    1. There should be exactly one node with no parent.
    2. Each node should have at most one parent. In other words, a node cannot have multiple parents.
    3. The tree should be connected, meaning you should be able to visit all nodes starting from any node.

If these conditions are met, return `true`. Otherwise, return `false`.

**Input**:

- `n` - The number of binary tree nodes.
- `leftChild` - An array of size `n`, where `leftChild[i]` is the left child of node `i`. If a node doesn't have a left child, `leftChild[i]` is set to -1.
- `rightChild` - An array of size `n`, where `rightChild[i]` is the right child of node `i`. If a node doesn't have a right child, `rightChild[i]` is set to -1.

**Output**:

- Return `true` if the given nodes form a valid binary tree, and `false` otherwise.

## Example

### Example 1:

**Input**:

```
n = 4
leftChild = [1, -1, 3, -1]
rightChild = [2, -1, -1, -1]
```

**Output**:

```
true
```

In this example, the given nodes form a valid binary tree. There is one node with no parent, and all nodes are connected.

### Example 2:

**Input**:

```
n = 4
leftChild = [1, -1, 3, -1]
rightChild = [2, 3, -1, -1]
```

**Output**:

```
false
```

In this example, the given nodes do not form a valid binary tree. Node 3 has multiple parents.

## Constraints

- 1 <= `n` <= 10^4
- -1 <= `leftChild[i], rightChild[i]` <= `n - 1`

## Approach

To check if the given nodes form a valid binary tree, you can follow these steps:

1. Create an array `parent` of size `n` to keep track of the parent of each node. Initialize all elements in the array to -1, indicating that no node has a parent initially.

2. Iterate through the `leftChild` and `rightChild` arrays to find the parent of each node. For each node `i`, if `leftChild[i]` is not -1 (indicating it has a left child), check if it already has a parent. If it does, return `false` because a node cannot have multiple parents. If it doesn't have a parent, set `parent[leftChild[i]]` to `i`.

3. Repeat the same process for the right child, checking if it has a parent and assigning `parent[rightChild[i]]` to `i`.

4. After iterating through both `leftChild` and `rightChild` arrays, there should be exactly one node with no parent (i.e., its corresponding element in the `parent` array is still -1). If there is more than one node with no parent or no node with no parent, return `false`.

5. Finally, check if the graph is connected. You can do this by starting from any node and traversing the tree using Depth-First Search (DFS) or Breadth-First Search (BFS). If you visit all `n` nodes during the traversal, return `true`; otherwise, return `false`.

## Complexity

Space Complexity is O(n).
Time Complexity is O(n).
