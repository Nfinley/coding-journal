# Data Structures

- Index
  1.  [Trees](#trees)
  2.  [Hash Tables](#hash-tables)
  3.  [Linked Lists](#linked-lists)

# Trees

### Basics

- A Tree is a non-linear data structure composed of parent and child nodes.
- Each node contains a value and a list of references to its child nodes. Each tree has a root and leaf nodes
- Trees are useful for storing data that needs to be retrieved quickly or for representing hierarchical data.
  - EXAMPLES:
    1. The DOM is a tree with `<html>` as the root and the `<body>` as a child
    2. A phone contact list
    3. An org structure at a company
    4. Files system on a computer
- To Be Non-empty must satify 4 conditions:
  1. There needs to be exactly one root node
  2. Each node that is not root has only one parent
  3. You need to be able to reach each node by starting at root and following a sequence of `child` pointers
  4. A node at level `x` cannot have a child less than `x`. All children of a node have level of `x+1`.

### Important Terms

- Root: Top node of tree all other nodes are descendants of the root (root is the ancestor of all other nodes)
- Level: The level of node `X` is number of child pointers that need to be followed to get to `X` from the root
- Leaf: Nodes that do not have any child nodes
- Height of a tree: Max level in the tree - node furthest from the root
- Depth: Synonym for height for a tree
- Branching Factor: max number of children that any node has
- Balancing: Refers to inserting entries into a sorted tree in such a way that minimizes the tree's depth.

## Strengths & Weaknesses

**Strengths**

- Memory efficient and do not use more memory than they need to
- More flexible than simple arrays we can `balance` the tree
- Can naturally grow to hold arbitrary number of objects
- By keeping height of tree small in a sorted tree, searches can be very fast
- Heirachy of a tree is reflected in many problems we would try and model (see examples above)
- `Decision Trees` are a special type used to model the effects of different choices. The nodes are the state of the system; a node Y is a child of X if it is possible to make a single decision from state X to transform to state Y. Used when analyizing strategy games like chess.

**Weaknesses**

- Harder to debug
- Manipulations can require thorough understanding of recursion
- Have to make decisions how to balance the data based on expected use case and rearranging tree completely is expensive. Not good structure for sorting info about people if you expected users to sort by name or age.

## Tree Types

- Red-Black
- AVL (Adelson-Velsky and Landis): self-balancing binary search tree
- Binary Search Tree: Sorted tree with a branching factor of two (every node has at most two children). Requires that the left node has a value smaller than its parent and right node larger than its parent

## When to Use Trees

- You have data that is sorted in some way and you want to do a lot of searches on it.
- You need to manage objects that are clustered of objects that are grouped by some attribute. File systems are a common heirarchy in which nodes are either files or directories.
- You are trying to implement a search strategy such as backtracking

### Operations

[IMAGE OF BASIC OPERATIONS](http://res.cloudinary.com/thefinleycode/image/fetch/http://res.cloudinary.com/thefinleycode/image/upload/v1536156970/Screen_Shot_2018-09-04_at_7.29.04_AM_d9zogw.png)

References:

1. [CodeSignal](https://app.codesignal.com/interview-practice/topics/trees-basic/tutorial)
2. [Binary Search Tree Implementation](https://www.geeksforgeeks.org/implementation-binary-search-tree-javascript/)

## Binary Trees

- Binary Search Tree: Sorted tree with a branching factor of two (every node has at most two children). Requires that the left node has a value smaller than its parent and right node larger than its parent

- Definition for a binary tree node.
  ```javascript
  function TreeNode(val) {
    this.val = val;
    this.left = this.right = null;
  }
  ```
- Traversal Types: Breadth-first and Depth-frist
  -

## Hash Tables

- A data structure that implements an associative array abstract data type, a structure that can map keys to values.
- A hash table uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found.
- [WIKI](https://en.wikipedia.org/wiki/Hash_table)

## Linked Lists

[CodeSignal Lists](https://app.codesignal.com/interview-practice/topics/linked-lists/tutorial)

- A sequential-access data structure used to store ordered elements
- They prioritize quick and easy data insertion and deletion over item lookup
- Two types: Singly linked and Doubly linked

**Strengths**

- Linked lists store ordered lists of data in nodes.
- Linked lists allow for quick (O(1)) addition and removal of elements (advantage over an array).
- Linked lists can be resized dynamically.
- The size of a linked list is only limited by the amount of available memory.

**Weaknesses**

- Linked lists can require more space in memory than arrays do.
- Linked lists are sequential-access instead of random-access, meaning that accessing the ith element can be slow because you must iterate over i elements to get there.

```

```
