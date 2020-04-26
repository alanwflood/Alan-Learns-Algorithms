# B Trees

A Set of nodes interconnected to one another using a one way key/path system.

Every node has 0, 1 or 2 children (Thus Binary)
Child nodes are referred to as left or right child.

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

A child node that can be treated as a root node and as such become their own tree structure with child nodes, leafs and edges.

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

- Insert, delete and retrieve are in O(n) time
- Left child is always smaller than parent node
- Right child is always bigger than parent node

## Building a binary tree

### Insertions:

The logic to follow for insertions for Set Binary Tree (IE: no repeating values)
If rootNode is null the new value is the root node.
If value == data do nothing
If value is less than the node value and the leftChild is null insert it otherwise rerun logic on leftChild node
If value is greater than the node value and the rightChild is null insert it otherwise rerrun logic on rightChild node

## Searching:

Look at the root node value compared to the value you're looking for, if greater go right, if lower go left, if the left or right node is null, the value doesn't exist.

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

So there is 3 ways to traverse a binary tree, they each traverse nodes in a different order:
(a) Inorder (Left, Root, Right) - Return values in sorted order
(b) Preorder (Root, Left, Right) - Preorder traversal is used to create a copy of the tree.
(c) Postorder (Left, Right, Root) - Postorder traversal is used to delete the tree.

## Balancing Trees

Balanced trees are faster to navigate than unbalanced. Accessing values evaluates to O(log n) for balanced trees so how do we keep them balanced?
There are a few different ways

### ACL Trees

Depends on tracking the height of each node. (The max value of it's left and right childrens height + 1)

ACL specifies that heights of left + right children of every node to differ by at most +1

We balance the tree by ensuring the ACL contract is managed during the insertion and deletion methods by rotating a subtrees nodes.

With a tree of shape:

     41
    /  \

23 52
\
 31

On insertion of say 36, we have now voided the ACL contract, the left subtree is 3 while the right is 1.

We would balance the tree by rotating the values from this:

41
/ \
23 52
\
 31
\
 36

To this

41
/ \
31 52
/ \
23 36

In the event that you can't rotate the tree, you can swap a child node with the parent and then do the rotation, this is known as a double rotation.

You may need to do this for every node above the inserted one that has a violation after the insertion is complete.

Some checks:

If right child is right-heavy or balanced we can do a right rotation, vise versa for left;

Else we do two rotations. If the immediate child of the parent is heavier the opposite side so parent: Right Heavy, child: left heavy. We can do a double rotation to fix them.

### AVL Sort

- Insert N items O(n log n)
- Perform an in-order traversal O(n)
