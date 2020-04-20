# B Trees

A Set of nodes interconnected to one another using a one way key/path system.

Every node has 0, 1 or 2 children (Thus Binary)
Child  nodes are referred to as left or right child.

A B Tree is **not** cyclical, you can only have a path fo downards to a node from the root node.
A binary tree can only have **at most 2 child nodes per node**, it it's more it is not a valid binary tree.

They consist of roots, nodes, edges and leaves among other terminology.

### Root
Top level nodes that can have paths of 1 or 2 child nodes. Every non-root node has max 1 parent. The top level root has 0 parents and is the root of the whole tree.

### Leaf
A Child node that has no paths to another node is called a leaf. (Aka the end of the tree)

### Edge
A path/key creating a one way connetion to descending nodes.

### Subtrees
A child  node that can be treated as a root node and as such become their own tree structure with child nodes, leafs and edges.

### Depth
A count of how many edges a node is from the root path.

#### Root path
Path from the root to a specific node.

### Height
Longest possible path from a node to the furthest leaf. Leaf nodes always have a height of 0.

### Tree height
Longest possible path from the root node to a leaf.

**So:**
  Depth = Leaf to Root
  Height = Root to Leaf
  
### Full Tree
When every level is filled (Every node has 2 or 0 child nodes) including the last we conclude the tree is full.

### Complete Tree
When every level is filled but the last level, (A node could have 1 child) We conclude the tree is complete.

## Binary Search Trees

Using a binary tree data struture we can use it to hold searchable data.

By using a Binary tree:
  * Insert, delete and retrieve are in O(n) time
  * Left child is always smaller than parent node
  * Right child is always bigger than parent node


## Building a binary tree

### Insertions:
The logic to follow for insertions for Set Binary Tree (IE: no repeating values)
If rootNode is null the new value is the root node.
If value == data do nothing
If value is less than the node value and the leftChild is null insert it otherwise rerun logic on leftChild node
If value is greater than the node value and the rightChild is null insert it otherwise rerrun logic on rightChild node

### Min Values
Find the min is essentially just going down the left edges of the tree into you find a node with no left child.
Then you know that's the smallest possible value in the tree

### Max Values
Likewise to find the max it's essentially the same as min but do the rightside edges and when you find a node with no right child you know it's the largest value in the tree.

### Deleting value

First we go down the left or right edges to find the required value to delete and treat that value and it's children as a subtree then:

We replace the node to delete with it's left or right child if it has one child, or we simply delete it if it has none.

If it has two children, we replace the value with that of the smallest value on the right side and then delete that same value from the subtree. So you're basically finding the min value then doing a copy and replace, then cleaning up afterwards

### Traversing

So there is 3 ways to traverse a binary tree:
(a) Inorder (Left, Root, Right) - Return values in sorted order
(b) Preorder (Root, Left, Right) - Preorder traversal is used to create a copy of the tree. 
(c) Postorder (Left, Right, Root) - Postorder traversal is used to delete the tree.
