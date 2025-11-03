<h1>ExpNo 2 : Implement Depth First Search Traversal of a Graph</h1> 
<h3>Name: HARSHITHA V </h3>
<h3>Register Number:  212223230074   </h3>
<H3>Aim:</H3>
<p> To Implement Depth First Search Traversal of a Graph using Python 3.</p>
<h3>Theory:</h3>
<strong>Depth First Traversal </strong>(or DFS) for a graph is like Depth First Traversal of a tree. The only catch here is that, unlike trees, graphs may contain cycles (a node may be visited twice). Use a Boolean visited array to avoid processing a node more than once. A graph can have more than one DFS traversal. 
Depth-first search is an algorithm for traversing or searching trees or graph data structures. The algorithm starts at the root node (selecting some arbitrary node as the root node in the case of a graph) and explores as far as possible along each branch before backtracking.
Step 1: Initially, stack and visited arrays are empty.

 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/640b3c6f-3ac1-49a2-a955-68da9a71f446)


Queue and visited arrays are empty initially.
Stack and visited arrays are empty initially.
Step 2: Visit 0 and put its adjacent nodes which are not visited yet into the stack.
 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/86dcf7d9-1f9d-49b0-a821-5976a6e77606)

 Visit node 0 and put its adjacent nodes (1, 2, 3) into the stack
 Visit node 0 and put its adjacent nodes (1, 2, 3) into the stack

Step 3: Now, Node 1 at the top of the stack, so visit node 1 and pop it from the stack and put all of its adjacent nodes which are not visited in the stack.
 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/e6017942-08b1-4742-87ad-c97eb97bf985)

Visit node 1
 Visit node 1

Step 4: Now, Node 2 at the top of the stack, so visit node 2 and pop it from the stack and put all of its adjacent nodes which are not visited (i.e, 3, 4) in the stack.
 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/6e6d123c-60ae-4f9c-a27c-c4fc7e57d57c)

 Visit node 2 and put its unvisited adjacent nodes (3, 4) into the stack
 Visit node 2 and put its unvisited adjacent nodes (3, 4) into the stack

Step 5: Now, Node 4 at the top of the stack, so visit node 4 and pop it from the stack and put all of its adjacent nodes which are not visited in the stack.
 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/20b76a05-5668-4da5-8189-e10fb1bb7238)

 Visit node 4
 Visit node 4

Step 6: Now, Node 3 at the top of the stack, so visit node 3 and pop it from the stack and put all of its adjacent nodes which are not visited in the stack.
 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/3b88f04a-7846-4f75-89b4-22bbd5b48e52)

Visit node 3
Visit node 3

Now, the Stack becomes empty, which means we have visited all the nodes, and our DFS traversal ends.

<h3>Algorithm:</h3>
<B><ol>
 <li>Construct a Graph with Nodes and Edges</li>
 <li>Depth First Search Uses Stack and Recursion</li>
 <li>Insert a START node to the STACK</li>
 <li>Find its Successors Or neighbors and Check whether the node is visited or not</li>
 <li>If Not Visited, add it to the STACK. Else Call The Function Again Until No more nodes needs to be visited.</li>
</ol></B>

<hr>
<h3>Sample Input</h3>
<hr>
8 9 <BR>
A B <BR>
A C <BR>
B E <BR>
C D <BR>
B D <BR>
C G <BR>
D F <BR>
G F <BR>
F H <BR>
<hr>
<h3>Sample Output</h3>
<hr>
['A', 'B', 'E', 'D', 'C', 'G', 'F', 'H']

<hr>

<hr>
<h3>Sample Input</h3>
<hr>
5 5 <BR>
0 1 <BR>
0 2 <BR>
0 3 <BR>
2 3 <BR>
2 4 <BR>
<hr>
<h3>Sample Output</h3>
<hr>
['0', '1', '2', '3', '4']

<h3>program</h3>

```
from collections import defaultdict

def dfs(graph, node, visited, path):
    
    visited[node] = True
    path.append(node)
    for neighbor in sorted(graph[node]): 
        if not visited[neighbor]:
            dfs(graph, neighbor, visited, path)
    return path

def solve_dfs_traversal(data_lines):
    """Parses input data and executes the DFS function."""
    
    data_iter = iter(data_lines)
    try:
        v, e = map(int, next(data_iter).split())
    except StopIteration:
        print("Error: Missing V and E line.")
        return

    graph = defaultdict(list)
    for _ in range(e):
        try:
            u, v = next(data_iter).split()
            graph[u].append(v)
            graph[v].append(u)
        except StopIteration:
            print(f"Error: Expected {e} edges, but stopped at edge {_}.")
            return
        
    try:
        start = next(data_iter).strip()
    except StopIteration:
        try:
            start = next(data_iter).strip()
        except StopIteration:
            print("Error: Missing start node.")
            return

    visited = defaultdict(bool)
    path = []
    
    traversedpath = dfs(graph, start, visited, path)
    return traversedpath

sample_input_1 = [
    "8 9",
    "A B",
    "A C",
    "B E",
    "C D",
    "B D",
    "C G",
    "D F",
    "G F",
    "F H",
    "A" 
]
print(solve_dfs_traversal(sample_input_1))
sample_input_2 = [
    "5 5",
    "0 1",
    "0 2",
    "0 3",
    "2 3",
    "2 4",
    "0"
]
print(solve_dfs_traversal(sample_input_2))
```

<h3>Output</h3>

<img width="388" height="53" alt="image" src="https://github.com/user-attachments/assets/f5d2707c-abdb-4fac-847c-44a2f4373fb9" />

<hr>
<h3>Result:</h3>
<hr>
<p>Thus,a Graph was constructed and implementation of Depth First Search for the same graph was done successfully.</p>

