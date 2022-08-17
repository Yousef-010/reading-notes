# Reading 29 : Graphs 


> what is Graph 
- A graph is a non-linear data structure that can be looked at as a collection of vertices (or nodes) potentially connected by line segments named edges.

> Terminologies when use graph  
- Vertex
  - vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
- Edge
  - An edge is a connection between two nodes.
- Neighbor 
  - The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
- Degree 
  - The degree of a vertex is the number of edges connected to that vertex.

> Undirected Graphs 
- is a graph where each edge is undirected or bi-directional.

> Directed Graphs 
- is a graph where every edge is directed.

> Complete Graphs 
- A complete graph is when all nodes are connected to all other nodes.

> Connected
- A connected graph is graph that has all of vertices/nodes have at least one edge.

> Disconnected
- A disconnected graph is a graph where some vertices may not have edges.

> Acyclic Graph
- An acyclic graph is a directed graph without cycles. 
- A cycle is when a node can be traversed through and potentially end up back at itself.
- A directed acyclic graph is also called a DAG. This can also be represented as what we know as a tree

> Cyclic Graphs 
- graph is a graph that has cycles.
- A cycle is defined as a path of a positive length that starts and ends at the same vertex.

> Graph Representation 
- Adjacency Matrix
  - is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix
  - a sparse graph is when there are very few connections. a dense graph is when there are many connections
- Adjacency List
  - is the most common way to represent graphs. 
  - is a collection of linked lists or array that lists all of the other vertices that are connected

> Weighted Graphs
- is a graph with numbers assigned to its edges. These numbers are called weights

> Traversals
- Breadth First
  - you are starting at a specific vertex/node
  - This node must be specified when calling the BreadthFirst() method.
  - like the breadth-first in the trees but with the exception that graphs can have cycles. 

> algorithm breadth first traversal :
- Enqueue the declared start node into the Queue.
- Create a loop that will run while the node still has nodes present.
- Dequeue the first node from the queue
- if the Dequeue‘d node has unvisited child nodes, add the unvisited children to visited set and insert them into the queue.

> Pseudocode for breadth-first algorithm
```
ALGORITHM BreadthFirst(vertex)
    DECLARE nodes <-- new List()
    DECLARE breadth <-- new Queue()
    DECLARE visited <-- new Set()

    breadth.Enqueue(vertex)
    visited.Add(vertex)

    while (breadth is not empty)
        DECLARE front <-- breadth.Dequeue()
        nodes.Add(front)

        for each child in front.Children
            if(child is not visited)
                visited.Add(child)
                breadth.Enqueue(child)

    return nodes;
```
> Steps for the above algorithm
- We have declared that our starting node (or root) is going to be Node A.
- The first thing we want to do is Enqueue the root.
- We also need to add the root to the visited set.
- Next, we enter a while loop. We want this loop to keep running until there are no more nodes in our queue.
- Once we are in the while loop, we want to Dequeue the front node and then check to see if it has any children.
- if there are children of the node we are currently looking at, we want to add them to visited set. This will help us know that we have already seen that node before, and won’t accidently push us into an infinite loop if the graph was cyclic. In addition to tracking each child node as visited, we want to place any of its children that have not yet been visited into the queue.
- The process will complete until the queue is empty.
- Once the while loop breaks, we can then return the list of nodes. This list will contain, in order, all the nodes that were traversed.

> Notest about breadth-first traversing 
- _If there are any disconnected nodes (such as islands) with the graph data structure, they will not be traversed._
- _Breadth first only outputs the nodes that are connected in some relation to the root that you pass in._

> Depth First
- While the breadth first traversal uses a Queue to visit all children at a given level
- the depth first traversal uses a Stack to visit all children of a given subtree.

> depth first traversal:
- Push the root node into the Stack and mark as visited.
- Start a while loop that runs as long as the stack is not empty.
- Pop the top node off of the stack and check its neighbors.
- If a neighbor hasn’t been visited, push it onto the stack and mark as visited.
- Repeat until the stack is empty.


![image](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/Depth1.PNG)


> Steps for depth traverse: 
- We start by adding our root Node (Node A) to the Stack and marking it as visited. 
- we want to initiate our loop and begin Popping Nodes off the Stack.
- We pop off our root Node and check its neighbors, as neither have been visited. We then push both Node B and Node D onto the Stack and mark them as visited.
- depending on the order in which Nodes B and D have been added as neighbors, we assume that Node B is the top Node ready to Pop off and be evaluated.
- We pop off Node B and check its neighbors: Node C, which has not been visited so we add it to the top of the Stack and mark as visited.
- As our Stack is not empty, we continue to Pop nodes from the top of our stack, by the time we hit Node G this is the state of our data structure:
- Now that we have visited all the neighbors of one sub child, the top of our stack contains Node D, the other neighbor of our root node.
- pop off Node D and check it’s neighbors to add them to our Stack.
- Again, depending on the order in which these Nodes were added as neighbors to Node D, we should check Nodes
- With Node E sitting at the top of the Stack, we pop it off the Stack and check it’s neighbors. There is only one, Node D.
- Since Node D has already been visited, we can ignore it and Pop the next node off the Stack: Node H.
- We check the neighbors for Node H and notice that both Nodes D and F have previously been visited, so neither are added to the Stack.
- Finally we Pop off Node F, and again notice that both neighbors Node D and Node H have already been visited, so we don’t add anything to our Stack.

> How we can use Graph in real-time
- GPS and Mapping
- Driving Directions
- Social Networks
- Airline Traffic
- Netflix uses graphs for suggestions of products


> Resources 
- https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/graphs.html