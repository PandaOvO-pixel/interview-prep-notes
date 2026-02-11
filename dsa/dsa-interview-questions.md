# Data Structures and Algorithms - Interview Questions & Answers

## 1. What are Data Structures?

**Answer:** Data structures are specialized formats for organizing, processing, storing, and retrieving data efficiently.

**Why Important:**
- Efficient data management
- Better performance
- Code optimization
- Problem-solving foundation

**Categories:**
- **Linear:** Array, Linked List, Stack, Queue
- **Non-Linear:** Tree, Graph
- **Hash-based:** Hash Table, Hash Map

---

## 2. What is the difference between Array and Linked List?

**Answer:**

| Feature | Array | Linked List |
|---------|-------|-------------|
| Memory | Contiguous | Non-contiguous |
| Size | Fixed (static arrays) | Dynamic |
| Access Time | O(1) - Direct | O(n) - Sequential |
| Insertion/Deletion | O(n) - Shifting required | O(1) - Update pointers |
| Memory Usage | Less | More (stores pointers) |
| Cache Performance | Better | Poor |

**When to use:**
- Array: Random access needed, size known
- Linked List: Frequent insertions/deletions, size unknown

---

## 3. What are the types of Linked Lists?

**Answer:**

**1. Singly Linked List:**
- Each node points to next node
- Unidirectional traversal
- Less memory

**2. Doubly Linked List:**
- Each node points to next and previous
- Bidirectional traversal
- More memory (two pointers)

**3. Circular Linked List:**
- Last node points to first node
- Forms a circle
- No null pointer

**4. Circular Doubly Linked List:**
- Combination of doubly and circular
- Both directions, circular

---

## 4. What is a Stack and where is it used?

**Answer:** Stack is a linear data structure following LIFO (Last In First Out) principle.

**Operations:**
- **Push:** Add element to top - O(1)
- **Pop:** Remove element from top - O(1)
- **Peek/Top:** View top element - O(1)
- **isEmpty:** Check if empty - O(1)

**Real-world Applications:**
- Function call stack (recursion)
- Undo/Redo operations
- Browser back button
- Expression evaluation
- Backtracking algorithms
- Syntax parsing

**Interview Tip:** Last element added is first to be removed.

---

## 5. What is a Queue and its types?

**Answer:** Queue is a linear data structure following FIFO (First In First Out) principle.

**Basic Operations:**
- **Enqueue:** Add element to rear - O(1)
- **Dequeue:** Remove element from front - O(1)
- **Front:** View front element - O(1)
- **isEmpty:** Check if empty - O(1)

**Types:**

**1. Simple Queue:** Basic FIFO
**2. Circular Queue:** Last position connected to first
**3. Priority Queue:** Elements have priorities
**4. Deque (Double-ended Queue):** Insert/delete from both ends

**Applications:**
- CPU scheduling
- Printer queue
- BFS traversal
- Request handling

---

## 6. What is the difference between Stack and Queue?

**Answer:**

| Feature | Stack | Queue |
|---------|-------|-------|
| Principle | LIFO (Last In First Out) | FIFO (First In First Out) |
| Operations | Push, Pop | Enqueue, Dequeue |
| Pointer | One (top) | Two (front, rear) |
| Use Case | Recursion, undo | Scheduling, BFS |

---

## 7. What is a Binary Tree?

**Answer:** Binary Tree is a hierarchical data structure where each node has at most two children (left and right).

**Terminology:**
- **Root:** Top node
- **Parent:** Node with children
- **Child:** Node below parent
- **Leaf:** Node with no children
- **Height:** Longest path from root to leaf
- **Depth:** Distance from root to node

**Types:**
1. **Full Binary Tree:** Each node has 0 or 2 children
2. **Complete Binary Tree:** All levels filled except possibly last
3. **Perfect Binary Tree:** All internal nodes have 2 children, all leaves at same level
4. **Balanced Binary Tree:** Height difference of subtrees ≤ 1

---

## 8. What is a Binary Search Tree (BST)?

**Answer:** BST is a binary tree where:
- Left subtree values < node value
- Right subtree values > node value
- Both subtrees are also BSTs

**Operations:**
- **Search:** O(log n) average, O(n) worst
- **Insert:** O(log n) average, O(n) worst
- **Delete:** O(log n) average, O(n) worst

**Advantages:**
- Fast search operations
- Ordered data
- Dynamic size

**Disadvantage:** Can become skewed (unbalanced), degrading to O(n)

**Interview Tip:** Inorder traversal of BST gives sorted order.

---

## 9. What are Tree Traversal methods?

**Answer:**

**1. Inorder (Left-Root-Right):**
- Used for BST to get sorted order
- Logic: Visit left → process node → visit right

**2. Preorder (Root-Left-Right):**
- Used to create copy of tree
- Logic: Process node → visit left → visit right

**3. Postorder (Left-Right-Root):**
- Used to delete tree
- Logic: Visit left → visit right → process node

**4. Level Order (BFS):**
- Level by level traversal
- Uses queue
- Logic: Process level by level from left to right

---

## 10. What is the difference between BFS and DFS?

**Answer:**

| Feature | BFS (Breadth-First) | DFS (Depth-First) |
|---------|-------------------|-------------------|
| Data Structure | Queue | Stack (or recursion) |
| Traversal | Level by level | Deep dive first |
| Memory | More | Less |
| Path Finding | Shortest path | Any path |
| Time Complexity | O(V + E) | O(V + E) |

**When to use:**
- **BFS:** Shortest path, level-order, web crawling
- **DFS:** Topological sort, cycle detection, maze solving

---

## 11. What is a Hash Table?

**Answer:** Hash Table is a data structure that stores key-value pairs using a hash function to compute index.

**Components:**
- **Hash Function:** Converts key to index
- **Buckets/Slots:** Array positions
- **Collision Handling:** Resolve multiple keys mapping to same index

**Time Complexity:**
- **Average:** O(1) for search, insert, delete
- **Worst:** O(n) with many collisions

**Collision Resolution:**
1. **Chaining:** Linked list at each index
2. **Open Addressing:** Find next available slot
   - Linear probing
   - Quadratic probing
   - Double hashing

---

## 12. What is Hashing?

**Answer:** Hashing is the process of converting data of any size into fixed-size value (hash) using a hash function.

**Properties of Good Hash Function:**
- Deterministic (same input → same output)
- Uniform distribution
- Fast computation
- Minimize collisions

**Applications:**
- Hash tables
- Password storage
- Data integrity verification
- Cryptography
- Caching

---

## 13. What is the difference between Heap and Priority Queue?

**Answer:**

**Heap:**
- Complete binary tree structure
- Max-Heap: Parent ≥ children
- Min-Heap: Parent ≤ children
- Implementation structure

**Priority Queue:**
- Abstract data type
- Elements have priorities
- Higher priority served first
- Can be implemented using heap

**Relationship:** Priority Queue is often implemented using Heap for efficiency.

---

## 14. What are Sorting Algorithms and their complexities?

**Answer:**

| Algorithm | Best | Average | Worst | Space | Stable |
|-----------|------|---------|-------|-------|--------|
| Bubble Sort | O(n) | O(n²) | O(n²) | O(1) | Yes |
| Selection Sort | O(n²) | O(n²) | O(n²) | O(1) | No |
| Insertion Sort | O(n) | O(n²) | O(n²) | O(1) | Yes |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) | Yes |
| Quick Sort | O(n log n) | O(n log n) | O(n²) | O(log n) | No |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | O(1) | No |

**Interview Tip:** Merge sort for linked lists, Quick sort for arrays (in-place).

---

## 15. Explain Quick Sort algorithm.

**Answer:** Quick Sort is a divide-and-conquer algorithm that picks a pivot element and partitions array around it.

**Steps:**
1. Choose pivot element
2. Partition: Elements < pivot on left, > pivot on right
3. Recursively sort left and right partitions

**Time Complexity:**
- Best/Average: O(n log n)
- Worst: O(n²) - when array already sorted

**Space:** O(log n) - recursion stack

**Advantages:**
- In-place sorting
- Fast for large datasets
- Cache efficient

**Interview Tip:** Pivot selection strategy affects performance. Randomized pivot helps avoid worst case.

---

## 16. Explain Merge Sort algorithm.

**Answer:** Merge Sort is a divide-and-conquer algorithm that divides array into halves, sorts them, and merges back.

**Steps:**
1. Divide array into two halves
2. Recursively sort both halves
3. Merge sorted halves

**Time Complexity:** O(n log n) - all cases
**Space:** O(n) - temporary arrays

**Advantages:**
- Stable sorting
- Predictable performance
- Good for linked lists

**Disadvantage:** Requires extra space

---

## 17. What is Binary Search?

**Answer:** Binary Search is an efficient algorithm to find element in sorted array by repeatedly dividing search interval in half.

**Steps:**
1. Compare target with middle element
2. If equal, return index
3. If target smaller, search left half
4. If target larger, search right half
5. Repeat until found or interval empty

**Requirements:** Array must be sorted

**Time Complexity:** O(log n)
**Space:** O(1) - iterative, O(log n) - recursive

**Interview Tip:** Always consider if array is sorted before suggesting binary search.

---

## 18. What is the difference between Linear Search and Binary Search?

**Answer:**

| Feature | Linear Search | Binary Search |
|---------|--------------|---------------|
| Requirement | Any array | Sorted array |
| Time (Best) | O(1) | O(1) |
| Time (Average) | O(n) | O(log n) |
| Time (Worst) | O(n) | O(log n) |
| Space | O(1) | O(1) |
| Approach | Sequential | Divide and conquer |

**When to use:**
- Linear: Small or unsorted data
- Binary: Large sorted data

---

## 19. What is a Graph?

**Answer:** Graph is a non-linear data structure consisting of vertices (nodes) and edges (connections).

**Types:**

**By Direction:**
- **Directed (Digraph):** Edges have direction
- **Undirected:** Edges have no direction

**By Weight:**
- **Weighted:** Edges have weights/costs
- **Unweighted:** Edges have no weights

**By Connection:**
- **Connected:** Path exists between all vertices
- **Disconnected:** Some vertices unreachable

**Representations:**
1. **Adjacency Matrix:** 2D array
2. **Adjacency List:** Array of lists

---

## 20. What is the difference between Tree and Graph?

**Answer:**

| Feature | Tree | Graph |
|---------|------|-------|
| Structure | Hierarchical | Network |
| Cycles | No cycles | Can have cycles |
| Root | Has root node | No root |
| Edges | N-1 edges (N nodes) | Any number |
| Path | One path between nodes | Multiple paths possible |
| Parent-Child | Yes | No |

**Interview Tip:** Tree is a special type of graph (connected acyclic graph).

---

## 21. What is Dynamic Programming?

**Answer:** Dynamic Programming (DP) is an optimization technique that solves complex problems by breaking them into overlapping subproblems and storing results.

**Key Characteristics:**
- **Overlapping Subproblems:** Same subproblems solved multiple times
- **Optimal Substructure:** Optimal solution built from optimal solutions of subproblems

**Approaches:**
1. **Memoization (Top-Down):** Recursion + caching
2. **Tabulation (Bottom-Up):** Iterative + table

**Classic Problems:**
- Fibonacci sequence
- Knapsack problem
- Longest common subsequence
- Coin change problem
- Matrix chain multiplication

---

## 22. What is the difference between Greedy and Dynamic Programming?

**Answer:**

| Feature | Greedy | Dynamic Programming |
|---------|--------|-------------------|
| Approach | Make locally optimal choice | Consider all possibilities |
| Guarantee | May not give optimal solution | Guarantees optimal solution |
| Efficiency | More efficient | Less efficient |
| Subproblems | No overlapping | Overlapping subproblems |
| Use Case | When greedy choice property holds | Optimization problems |

**Greedy Examples:** Dijkstra's, Huffman coding, Activity selection
**DP Examples:** Knapsack, LCS, Edit distance

---

## 23. What is Recursion and when to use it?

**Answer:** Recursion is a technique where function calls itself to solve smaller instances of same problem.

**Components:**
- **Base Case:** Stopping condition
- **Recursive Case:** Function calls itself

**Advantages:**
- Clean, elegant code
- Natural for problems with recursive structure
- Reduces code complexity

**Disadvantages:**
- Stack overflow risk
- Higher memory usage
- Slower than iteration

**Use Cases:**
- Tree/graph traversal
- Divide and conquer
- Backtracking
- Dynamic programming

---

## 24. What is Time Complexity?

**Answer:** Time complexity measures algorithm's execution time as function of input size.

**Common Complexities (Best to Worst):**
- **O(1):** Constant - Accessing array element
- **O(log n):** Logarithmic - Binary search
- **O(n):** Linear - Single loop
- **O(n log n):** Linearithmic - Merge sort, Quick sort
- **O(n²):** Quadratic - Nested loops
- **O(2ⁿ):** Exponential - Recursive Fibonacci
- **O(n!):** Factorial - Traveling salesman (brute force)

**Interview Tip:** Always analyze best, average, and worst case complexities.

---

## 25. What is Space Complexity?

**Answer:** Space complexity measures memory used by algorithm as function of input size.

**Components:**
- **Auxiliary Space:** Extra space used by algorithm
- **Input Space:** Space for input data

**Examples:**
- O(1): Few variables, in-place operations
- O(n): Array/list of size n
- O(log n): Recursion stack in binary search
- O(n²): 2D matrix

**Interview Tip:** Consider both time and space trade-offs. Sometimes using more space improves time.

---

## 26. What is Big O Notation?

**Answer:** Big O notation describes upper bound of algorithm's growth rate (worst-case scenario).

**Variants:**
- **Big O (O):** Upper bound (worst case)
- **Big Omega (Ω):** Lower bound (best case)
- **Big Theta (Θ):** Tight bound (average case)

**Rules:**
- Drop constants: O(2n) → O(n)
- Drop lower terms: O(n² + n) → O(n²)
- Consider dominant term

---

## 27. What is a Trie?

**Answer:** Trie (prefix tree) is a tree-like data structure for storing strings where each node represents a character.

**Properties:**
- Root is empty
- Each path represents a word
- Common prefixes share nodes

**Operations:**
- **Insert:** O(m) - m is word length
- **Search:** O(m)
- **Delete:** O(m)

**Applications:**
- Autocomplete
- Spell checker
- IP routing
- Dictionary implementation

**Advantage:** Fast prefix-based searches

---

## 28. What is AVL Tree?

**Answer:** AVL Tree is a self-balancing Binary Search Tree where height difference between left and right subtrees is at most 1.

**Balance Factor:** Height(left subtree) - Height(right subtree)
- Allowed values: -1, 0, 1

**Rotations:**
- Left Rotation
- Right Rotation
- Left-Right Rotation
- Right-Left Rotation

**Time Complexity:** O(log n) for search, insert, delete (guaranteed)

**Use Case:** When frequent searches and guaranteed O(log n) performance needed

---

## 29. What is the difference between Array and ArrayList?

**Answer:**

| Feature | Array | ArrayList |
|---------|-------|-----------|
| Size | Fixed | Dynamic |
| Type | Primitives + Objects | Only Objects |
| Performance | Faster | Slightly slower |
| Dimension | Multi-dimensional | Single |
| Syntax | Built-in | Collection class |
| Length | `.length` property | `.size()` method |

---

## 30. What are common algorithm design techniques?

**Answer:**

**1. Brute Force:**
- Try all possibilities
- Simple but inefficient

**2. Divide and Conquer:**
- Break problem into subproblems
- Examples: Merge Sort, Quick Sort, Binary Search

**3. Dynamic Programming:**
- Store subproblem results
- Examples: Fibonacci, Knapsack

**4. Greedy:**
- Make locally optimal choice
- Examples: Dijkstra's, Huffman coding

**5. Backtracking:**
- Try solutions, backtrack if wrong
- Examples: N-Queens, Sudoku solver

**6. Branch and Bound:**
- Exploration with bounds
- Examples: Traveling salesman

**Interview Tip:** Choose technique based on problem characteristics and constraints.

---
## 31. What is time complexity and space complexity?

**Answer:**

**Time Complexity:**
- Measures execution time growth
- How algorithm scales with input size
- Expressed in Big O notation

**Space Complexity:**
- Measures memory usage growth
- Includes auxiliary space + input space
- Also expressed in Big O notation

**Trade-off:** Sometimes we sacrifice space for time or vice versa.

---

## 32. What is the difference between BFS and DFS?

**Answer:**

| BFS | DFS |
|-----|-----|
| Breadth First Search | Depth First Search |
| Uses Queue | Uses Stack (or recursion) |
| Level-by-level traversal | Path-by-path traversal |
| More memory usage | Less memory usage |
| Finds shortest path | Explores deeply first |
| FIFO | LIFO |

**BFS Use Cases:** Shortest path, level-order traversal, peer-to-peer networks
**DFS Use Cases:** Topological sorting, cycle detection, path finding

---

## 33. What is a priority queue?

**Answer:** Priority queue is abstract data type where each element has priority.

**Characteristics:**
- Elements served by priority, not insertion order
- Higher priority elements dequeued first
- Typically implemented using heap

**Operations:**
- Insert: Add with priority
- Extract-Max/Min: Remove highest/lowest priority
- Peek: View highest priority

**Use Cases:** Job scheduling, Dijkstra's algorithm, Huffman coding, event simulation

---

## 34. What is a trie?

**Answer:** Trie (prefix tree) is tree data structure for storing strings.

**Characteristics:**
- Each node represents character
- Root is empty
- Paths from root form strings
- Efficient for prefix operations

**Operations:**
- Insert: O(m) where m is string length
- Search: O(m)
- Prefix search: O(m)

**Use Cases:** Autocomplete, spell checker, IP routing, dictionary

---

## 35. What is hashing?

**Answer:** Hashing transforms input into fixed-size value using hash function.

**Characteristics:**
- Deterministic: Same input → same output
- Fixed output size
- Fast computation
- One-way (hard to reverse)

**Collision Handling:**
- **Chaining:** Store collisions in linked list
- **Open Addressing:** Find next empty slot (linear/quadratic probing, double hashing)

**Use Cases:** Hash tables, data integrity, password storage, caching

---

## 36. What is the difference between array and linked list?

**Answer:**

| Array | Linked List |
|-------|-------------|
| Contiguous memory | Non-contiguous memory |
| Fixed size | Dynamic size |
| Random access O(1) | Sequential access O(n) |
| Insert/delete O(n) | Insert/delete O(1) at position |
| Better cache locality | Poor cache locality |
| Less memory per element | More memory (stores pointers) |

**Choose Array:** When frequent access by index
**Choose Linked List:** When frequent insertions/deletions

---

## 37. What is recursion?

**Answer:** Recursion is when function calls itself to solve smaller instances of same problem.

**Components:**
- **Base Case:** Stopping condition
- **Recursive Case:** Function calls itself with smaller input

**Types:**
- **Direct:** Function calls itself
- **Indirect:** Function A calls B, B calls A

**Pros:** Clean code, natural for tree/graph problems
**Cons:** Stack overflow risk, memory overhead, sometimes slower

---

## 38. What is a balanced tree?

**Answer:** Balanced tree maintains height difference constraint between subtrees.

**Types:**
- **AVL Tree:** Height difference ≤ 1
- **Red-Black Tree:** Balanced using colors
- **B-Tree:** Multiple keys per node

**Benefits:**
- Guaranteed O(log n) operations
- No degradation to linked list
- Predictable performance

**Cost:** Extra operations for balancing during insertions/deletions

---

## 39. What is topological sorting?

**Answer:** Topological sorting is linear ordering of vertices in directed acyclic graph (DAG).

**Properties:**
- For edge u→v, u appears before v in ordering
- Only possible for DAGs (no cycles)
- Multiple valid orderings possible

**Algorithms:**
- Kahn's Algorithm (BFS-based)
- DFS-based approach

**Use Cases:** Task scheduling, course prerequisites, build systems, dependency resolution

---

## 40. What is dynamic programming?

**Answer:** Dynamic programming solves problems by breaking into overlapping subproblems and storing results.

**Approaches:**
- **Top-Down (Memoization):** Recursion + caching
- **Bottom-Up (Tabulation):** Iterative, fill table

**Requirements:**
- Optimal substructure: Solution contains optimal solutions to subproblems
- Overlapping subproblems: Same subproblems solved multiple times

**Use Cases:** Fibonacci, Knapsack, Longest Common Subsequence, Matrix Chain Multiplication

---

## 41. What is a heap?

**Answer:** Heap is complete binary tree satisfying heap property.

**Types:**
- **Max Heap:** Parent ≥ children
- **Min Heap:** Parent ≤ children

**Properties:**
- Complete binary tree
- O(log n) insertion and deletion
- O(1) to find max/min
- Array representation efficient

**Use Cases:** Priority queue, heap sort, finding k largest/smallest elements

---

## 42. What is the difference between stack and queue?

**Answer:**

| Stack | Queue |
|-------|-------|
| LIFO (Last In First Out) | FIFO (First In First Out) |
| Push/Pop operations | Enqueue/Dequeue operations |
| One end (top) | Two ends (front/rear) |
| Undo mechanism | Task scheduling |
| Function call stack | Breadth-first search |

**Stack:** Recent items accessed first
**Queue:** Oldest items accessed first

---

## 43. What is binary search?

**Answer:** Binary search finds element in sorted array by repeatedly dividing search interval in half.

**Algorithm:**
1. Compare target with middle element
2. If match, return position
3. If target smaller, search left half
4. If target larger, search right half
5. Repeat until found or interval empty

**Complexity:** O(log n)
**Requirement:** Array must be sorted
**Advantage:** Very fast for large datasets

---

## 44. What is a circular linked list?

**Answer:** Circular linked list is linked list where last node points back to first node.

**Types:**
- **Singly Circular:** Last node points to first
- **Doubly Circular:** Last next → first, first prev → last

**Advantages:**
- No NULL pointers
- Can traverse entire list from any node
- Useful for round-robin scheduling

**Disadvantages:**
- Risk of infinite loops
- Slightly complex implementation

---

## 45. What is graph representation?

**Answer:**

**Adjacency Matrix:**
- 2D array of size V×V
- Matrix[i][j] = 1 if edge exists
- Space: O(V²)
- Edge check: O(1)
- Best for dense graphs

**Adjacency List:**
- Array of lists
- Each index stores adjacent vertices
- Space: O(V+E)
- Edge check: O(V)
- Best for sparse graphs

**Choice:** Depends on graph density and operations needed.

---