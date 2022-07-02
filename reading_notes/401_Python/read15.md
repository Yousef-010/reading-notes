# Reading 15 
## Explain a detail in depth for Trees in python 
> what is Trees
- In this tutorial, we’ll be covering Binary Trees, Binary Search Trees, and K-ary Trees.
- We will review some common terminology that is shared amongst all the trees and then dive into specifics of the different types.


> Common Terminology
- Node - A Tree node is a component which may contain its own values, and references to other nodes
- Root - The root is the node at the beginning of the tree
- K - A number that specifies the maximum number of children any node may have in a k-ary tree. In a binary tree, k = 2.
- Left - A reference to one child node, in a binary tree
- Right - A reference to the other child node, in a binary tree
- Edge - The edge in a tree is the link between a parent and child node
- Leaf - A leaf is a node that does not have any children
- Height - The height of a tree is the number of edges from the root to the furthest leaf


> Traversals 
- An important aspect of trees is how to traverse them. 
- Traversing a tree allows us to search for a node, print out the contents of a tree, and much more! There are two categories of traversals when it comes to trees: 
  - Depth First
    - Depth first traversal is where we prioritize going through the depth (height) of the tree first
    - Here are three methods for depth first traversal:
      - Pre-order: root >> left >> right
      - In-order: left >> root >> right
      - Post-order: left >> right >> root


> preorder code algorithm :
```
ALGORITHM preOrder(root)
  OUTPUT <-- root.value
  if root.left is not NULL
      preOrder(root.left)
  if root.right is not NULL
      preOrder(root.right)
```
> in-order code algorithm : 
```
ALGORITHM inOrder(root)
// INPUT <-- root node
// OUTPUT <-- in-order output of tree node's values
    if root.left is not NULL
        inOrder(root.left)
    OUTPUT <-- root.value
    if root.right is not NULL
        inOrder(root.right)
```

> post-order code algorithm :
```
ALGORITHM postOrder(root)
// INPUT <-- root node
// OUTPUT <-- post-order output of tree node's values
    if root.left is not NULL
        postOrder(root.left)
    if root.right is not NULL
        postOrder(root.right)
    OUTPUT <-- root.value
```

> Breadth First
- Breadth first traversal iterates through the tree by going through each level of the tree node-by-node. So, given our starting tree one more time:


> Code algorithm Breadth first:
```
ALGORITHM breadthFirst(root)
// INPUT  <-- root node
// OUTPUT <-- front node of queue to console
  Queue breadth <-- new Queue()
  breadth.enqueue(root)
  while ! breadth.is_empty()
    node front = breadth.dequeue()
    OUTPUT <-- front.value
    if front.left is not NULL
      breadth.enqueue(front.left)
    if front.right is not NULL
      breadth.enqueue(front.right)
```

> Binary Tree Vs K-ary Trees
- In all of our examples, we’ve been using a Binary Tree. Trees can have any number of children per node 
- but Binary Trees restrict the number of children to two (hence our left and right children).
  - Breadth First Traversal 
  - See the Resources for more information

> Pseudo code 
```
ALGORITHM breadthFirst(root)
// INPUT  <-- root node
// OUTPUT <-- front node of queue to console
  Queue breadth <-- new Queue()
  breadth.enqueue(root)
  while ! breadth.is_empty()
    node front = breadth.dequeue()
    OUTPUT <-- front.value
    for child in front.children
        breadth.enqueue(child)
```


> Adding a node
- Because there are no structural rules for where nodes are “supposed to go” in a binary tree, it really doesn’t matter where a new node gets placed.
  - One strategy for adding a new node to a binary tree is to fill all “child” spots from the top down. 
  - To do so, we would leverage the use of breadth first traversal.
  - During the traversal, we find the first node that does not have all its children filled,
  - and insert the new node as a child. We fill the child slots from left to right.


> Big O notation :
- The Big O time complexity for inserting a new node is O(n). 
- Searching for a specific node will also be O(n)
  - Because of the lack of organizational structure in a Binary Tree, the worst case for most operations will involve traversing the entire tree. 
  - If we assume that a tree has n nodes, then in the worst case we will have to look at n items, hence the O(n) complexity.
- big o for insertion 
  - The Big O space complexity for a node insertion using breadth first insertion will be O(w)
  - where w is the largest width of the tree. For example, in the above tree, w is 4.


> Binary Search Trees BST 
- A Binary Search Tree (BST) is a type of tree that does have some structure attached to it. 
- In a BST, nodes are organized in a manner where all values that are smaller than the root are placed to the left
- and all values that are larger than the root are placed to the right.
- Big o notation for BST 
  - The Big O time complexity of a Binary Search Tree’s insertion and search operations is O(h)
  - or O(height)
  - Wort case 
    - we will have to search all the way down to a leaf, which will require searching through as many nodes as the tree is tall.
  - balanced case 
    - In a balanced (or “perfect”) tree, the height of the tree is log(n). In an unbalanced tree, the worst case height of the tree is n.
  - Summary for big o for BST 
    - The Big O space complexity of a BST search would be O(1). During a search, we are not allocating any additional space.


> Resources 
- https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/C
