Breadth First Search is generally the best approach when the depth of the tree can vary, and you only need to search part of the tree for a solution. For example, finding the shortest path from a starting value to a final value is a good place to use BFS.

Depth First Search is commonly used when you need to search the entire tree. It's easier to implement (using recursion) than BFS, and requires less state: While BFS requires you store the entire 'frontier', DFS only requires you store the list of parent nodes of the current element.

