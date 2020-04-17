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
Long possible path from the root node to a leaf.

**So:**
  Depth = Leaf to Root
  Height = Root to Leaf
  
### Full Tree
When every level is filled (Every node has 2 child nodes) including the last we conclude the tree is full.

### Complete Tree
When every level is filled but the last level, (A node only has 1 or 0 children) We conclude the tree is complete.
