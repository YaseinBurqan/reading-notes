# Tree

## The types of Tree

- Binary Trees
- Binary Search Trees
- K-ary Trees

## Common Terminology

- Node - A Tree node is a component which may contain its own values, and references to other nodes
- Root - The root is the node at the beginning of the tree
- K - A number that specifies the maximum number of children any node may have in a k-ary tree. In a binary tree, k = 2.
- Left - A reference to one child node, in a binary tree
- Right - A reference to the other child node, in a binary tree
- Edge - The edge in a tree is the link between a parent and child node
- Leaf - A leaf is a node that does not have any children
- Height - The height of a tree is the number of edges from the root to the furthest leaf

![Sample Tree](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/images/BinaryTree1.PNG)

## An important aspect of trees is how to traverse them

- Depth First

Depth first traversal is where we prioritize going through the depth (height) of the tree first.

- Pre-order: root >> left >> right
- In-order: left >> root >> right
- Post-order: left >> right >> root

- Breadth First

Breadth first traversal iterates through the tree by going through each level of the tree node-by-node.

## Binary Tree Vs K-ary Trees

- Trees can have any number of children per node, but Binary Trees restrict the number of children to two (hence our left and right children).
- In all of our examples, we’ve been using a Binary Tree.
- Nodes can be added into a binary tree wherever space allows.

### K-ary Trees

- In this type of tree we use K to refer to the maximum number of children that each Node is able to have.
- If Nodes are able have more than 2 child nodes, we call the tree that contains them a K-ary Tree.

### Binary Search Trees

- In a BST, nodes are organized in a manner where all values that are smaller than the root are placed to the left, and all values that are larger than the root are placed to the right.
- A Binary Search Tree (BST) is a type of tree that does have some structure attached to it.
