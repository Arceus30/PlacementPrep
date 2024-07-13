# Algorithms

### 1. Recursion

-   when a function calls itself directly or indirectly
-   it has three parts :-
    -   Base Case
    -   Code to be executed by us or function body (Processing)
    -   Recursive code (Recursive Relation)
-   ```c++
    return_type recursive_function(parameters) {
        // Base case
        if (condition) {
            return base_value;
        }
        // Recursive call
        return recursive_function(modified_parameters);
    }
    ```

### 2. Searching

-   **Linear Search**
    -   ```c++
        function linearSearch(array, target):
            for each element in array:
                if element equals target:
                    return index of element
            return -1 // Element not found
        ```
-   **Binary Search**
    -   Applied on sorted arrays or some special cases of unsorted array. Binary Search can be used in questions where in an sorted search space we can neglect any part (left or right) of it using any condition.
    -   ```c++
        function binarySearch(array, target):
            left = 0
            right = size of array - 1
            while left <= right:
                mid = si + ( (ei-si) / 2 ) // this calculation method prevents overflow error
                if array[mid] equals target:
                    return mid
                else if array[mid] < target:
                    left = mid + 1
                else:
                    right = mid - 1
            return -1 // Element not found
        ```
-   **Interpolation Search**

    -   ```c++
        function interpolationSearch(array, target):
            low = 0
            high = size of array - 1
            while array[low] <= target and array[high] >= target:
                if low equals high:
                    if array[low] equals target:
                        return low
                    return -1 // Element not found
                pos = low + ((target - array[low]) * (high - low)) / (array[high] - array[low])
                if array[pos] equals target:
                    return pos
                else if array[pos] < target:
                    low = pos + 1
                else:
                    high = pos - 1
            return -1 // Element not found
        ```

### 3. Sorting

-   **Selection Sort:**
    -   It is used when array size is small and there are memory constraints
    -   ```c++
        function selectionSort(array):
            n = size of array
            for i from 0 to n-1:
            min_index=i
            for j from i+1 to n-1:
                if array[j] < array[min_index]:
                    min_index=j
            swap(array[i],array[min_index])
        ```
-   **Bubble Sort**
    -   It is used when there is a need to either find ith largest element or place ith largest element at its right location
    -   ```c++
        function bubbleSort(array):
            n = size of array
            for i from 0 to n-1:
                for j from 0 to n-i-1:
                    if array[j] > array[j+1]:
                        swap(array[j], array[j+1])
        ```
-   **Insertion Sort**

    -   This sorting technique is dynamic in nature the array is getting partially sorted as the number of iterations passed
    -   ```c++
        function insertionSort(array):
            n = size of array
            for i from 1 to n-1:
                key = array[i]
                j = i - 1
                while j >= 0 and array[j] > key:
                    array[j + 1] = array[j]
                    j = j - 1
                array[j + 1] = key

        ```

-   **Merge Sort**

    -   ```c++
        function mergeSort(array):
            if size of array > 1:
                mid = size of array / 2
                left_array = array[0 to mid-1]
                right_array = array[mid to end]
                mergeSort(left_array)
                mergeSort(right_array)
                merge(left_array, right_array, array)

        function merge(left_array, right_array, array):
            i = 0
            j = 0
            k = 0
            while i < size of left_array and j < size of right_array:
                if left_array[i] <= right_array[j]:
                    array[k] = left_array[i]
                    i = i + 1
                else:
                    array[k] = right_array[j]
                    j = j + 1
                k = k + 1
            while i < size of left_array:
                array[k] = left_array[i]
                i = i + 1
                k = k + 1
            while j < size of right_array:
                array[k] = right_array[j]
                j = j + 1
                k = k + 1
        ```

-   **Quick Sort**

    -   ```c++
        function quickSort(array, low, high):
            if low < high:
                pivot_index = partition(array, low, high)
                quickSort(array, low, pivot_index - 1)
                quickSort(array, pivot_index + 1, high)

        function partition(array, low, high):
            pivot = array[high]
            i = low - 1
            for j from low to high-1:
                if array[j] <= pivot:
                    i = i + 1
                    swap(array[i], array[j])
            swap(array[i + 1], array[high])
            return i + 1
        ```

-   **Heap Sort**

    -   ```c++
        function heapSort(array):
            buildMaxHeap(array)
            for i from size of array - 1 down to 1:
                swap(array[0], array[i])
                maxHeapify(array, 0, i)

        function buildMaxHeap(array):
            n = size of array
            for i from n/2 - 1 down to 0:
                maxHeapify(array, i, n)

        function maxHeapify(array, i, heapSize):
            largest = i
            left = 2*i + 1
            right = 2*i + 2
            if left < heapSize and array[left] > array[largest]:
                largest = left
            if right < heapSize and array[right] > array[largest]:
                largest = right
            if largest != i:
                swap(array[i], array[largest])
                maxHeapify(array, largest, heapSize)
        ```

-   **Bucket Sort**
    -   ```c++
        function bucketSort(array):
            min_val = minimum value in array
            max_val = maximum value in array
            bucket_count = max_val - min_val + 1
            buckets[bucket_count]
            for i from 0 to size of array - 1:
                index = (array[i] - min_val) / bucket_count
                buckets[index].append(array[i])
            sorted_index = 0
            for i from 0 to bucket_count - 1:
                sort(buckets[i])
                for j from 0 to size of buckets[i] - 1:
                    array[sorted_index] = buckets[i][j]
                    sorted_index = sorted_index + 1
        ```
-   **Radix Sort**

    -   ```c++
        function radixSort(array):
            max_digits = maximum number of digits in array
            for digit_position from 0 to max_digits - 1:
                countingSort(array, digit_position)

        function countingSort(array, digit_position):
            counts[10] = {0}
            for i from 0 to size of array - 1:
                digit = getDigit(array[i], digit_position)
                counts[digit] = counts[digit] + 1
            for i from 1 to 9:
                counts[i] = counts[i] + counts[i - 1]
            sorted_array[size of array]
            for i from size of array - 1 down to 0:
                digit = getDigit(array[i], digit_position)
                sorted_array[counts[digit] - 1] = array[i]
                counts[digit] = counts[digit] - 1
            for i from 0 to size of array - 1:
                array[i] = sorted_array[i]

        function getDigit(number, digit_position):
            return (number / 10^digit_position) % 10
        ```

-   **Counting Sort**

    -   ```c++
        function countingSort(array):
            min_val = minimum value in array
            max_val = maximum value in array
            counts[max_val - min_val + 1] = {0}
            for i from 0 to size of array - 1:
                counts[array[i] - min_val] = counts[array[i] - min_val] + 1
            for i from 1 to max_val - min_val:
                counts[i] = counts[i] + counts[i - 1]
            sorted_array[size of array]
            for i from size of array - 1 down to 0:
                sorted_array[counts[array[i] - min_val] - 1] = array[i]
                counts[array[i] - min_val] = counts[array[i] - min_val] - 1
            for i from 0 to size of array - 1:
                array[i] = sorted_array[i]
        ```

-   **Sorting Table**

| Name           | Best Case | Average Case | Worst Case | Memory | Stable |
| -------------- | --------- | ------------ | ---------- | ------ | ------ |
| Selection Sort | n^2       | n^2          | n^2        | 1      | No     |
| Bubble Sort    | n         | n^2          | n^2        | 1      | Yes    |
| Insertion Sort | n         | n^2          | n^2        | 1      | Yes    |
| Merge Sort     | n\*log(n) | n\*log(n)    | n\*log(n)  | n      | Yes    |
| Quick Sort     | n\*log(n) | n\*log(n)    | n^2        | log(n) | No     |
| Tim Sort       | n         | n\*log(n)    | n\*log(n)  | n      | Yes    |
| Heap Sort      | n\*log(n) | n\*log(n)    | n\*log(n)  | 1      | No     |
| Tree Sort      | n\*log(n) | n\*log(n)    | n\*log(n)  | n      | Yes    |
| Shell Sort     | n\*log(n) | n^(4/3)      | n^(3/2)    | 1      | No     |
| Bucket Sort    | n+k       | n+k          | n^2        | n+k    | Yes    |
| Radix Sort     | d\*(n+b)  | d\*(n+b)     | d\*(n+b)   | n+b    | Yes    |
| Counting Sort  | n+k       | n+k          | n+k        | n      | Yes    |

, where n = number of elements, k = number of buckets, d = number of digits, b = base

-   Stable sorting algorithms preserve the relative ordering of equal elements.
-   Optimal Choices:

    -   For small arrays (2 to 11): Insertion Sort
    -   For medium arrays (60 to 250): STL sort or Quicksort
    -   For large arrays (100k to 200k): Radix Sort

-   **Topological Sort (Graphs)**
    -   linear ordering of vertices such that for every directed edge u -> v, where vertex u comes before v in the ordering.
    -   Kahn's Algo
        -   we can also
            -   detect cycle
            -   find shortest distance
        -   ```c++
            // Kahn's algorithm for topological sorting
            function topologicalSort(graph):
                // Initialize an array to store in-degree of vertices
                inDegree = array of size graph.V initialized to 0
                // Initialize a queue to store vertices with in-degree of 0
                queue = empty queue
                // Initialize a list to store the sorted vertices
                sortedList = empty list
                // Calculate in-degree of each vertex
                for each vertex v in graph:
                    for each neighbor u of v:
                        inDegree[u]++
                // Enqueue vertices with in-degree of 0
                for each vertex v in graph:
                    if inDegree[v] == 0:
                        queue.enqueue(v)
                // Perform topological sorting
                while queue is not empty:
                    // Dequeue a vertex from the queue
                    currentVertex = queue.dequeue()
                    // Add the vertex to the sorted list
                    sortedList.append(currentVertex)
                    // Decrease in-degree of neighbors of the current vertex
                    for each neighbor u of currentVertex:
                        inDegree[u]--
                        // If in-degree becomes 0, enqueue the vertex
                        if inDegree[u] == 0:
                            queue.enqueue(u)
                // If the graph contains a cycle, sortedList will not contain all vertices
                if size of sortedList != graph.V:
                    print("The graph contains a cycle")
                else:
                    return sortedList
            ```

### 4. BackTracking

-   Backtracking is a problem-solving algorithmic technique that involves finding a solution incrementally by trying different options and undoing them if they lead to a dead end.
-   ```cpp
    void FIND_SOLUTIONS( parameters):
        if (valid solution):
            store the solution
            Return
        for (all choice):
            if (valid choice):
                APPLY (choice)
                FIND_SOLUTIONS (parameters)
                BACKTRACK (remove choice)
        Return
    ```

### 5. Dynamic Programming

-   Dynamic Programming is a method used to solve complex problems by solving each subproblem only once and storing the results, it avoids redundant computations, leading to more efficient solutions for a wide range of problems.

### 6. Floyd's Cycle Detection Algo

-   used to detect cycles in linked lists
-   ```c++
    function detectCycle(head):
        // Initialize two pointers: slow and fast
        slow = head
        fast = head

        // Traverse the list using two pointers
        while fast is not null and fast.next is not null:
            // Move slow pointer by one step
            slow = slow.next
            // Move fast pointer by two steps
            fast = fast.next.next
            // If slow and fast pointers meet, there is a cycle
            if slow equals fast:
                // Reset one of the pointers to the head
                slow = head
                // Move both pointers at the same pace until they meet again
                while slow is not fast:
                    slow = slow.next
                    fast = fast.next
                // Return the node where the cycle begins
                return slow

        // If fast pointer reaches the end, there is no cycle
        return null
    ```

### 7. Traversal

-   **PreOrder traversal**: Node, Left, Right
-   **InOrder traversal**: Left, Node, Right
-   **PostOrder traversal**: Left, Right, Node
-   **Boundary Traversal**:

    -   left boundary (nodes on left excluding leaf nodes), leaves (consist of only the leaf nodes), right boundary (nodes on right excluding leaf nodes)
    -   ```c++
            // Function to perform boundary traversal of a binary tree
            void boundaryTraversal(TreeNode* root) {
                if (root) {
                    // Print the root node's value
                    cout << root->val << " ";

                    // Traverse the left boundary (excluding leaves)
                    TreeNode* current = root->left;
                    while (current && (current->left || current->right)) {
                        cout << current->val << " ";
                        if (current->left)
                            current = current->left;
                        else
                            current = current->right;
                    }

                    // Traverse the leaves (bottom-up)
                    printLeaves(root);

                    // Traverse the right boundary (excluding leaves)
                    current = root->right;
                    vector<int> rightBoundary;
                    while (current && (current->left || current->right)) {
                        rightBoundary.push_back(current->val);
                        if (current->right)
                            current = current->right;
                        else
                            current = current->left;
                    }

                    // Print the right boundary nodes in reverse order
                    for (int i = rightBoundary.size() - 1; i >= 0; --i)
                        cout << rightBoundary[i] << " ";
                }
            }
        ```

-   **Morris Traversal**:
    -   We can traverse the tree without using stack and recursion.
    -   For PreOrder Traversal
        -   ```c++
                current = root
                While current != NULL
                    If the current.left == NULL
                        visit(current)
                        current = current->right
                    Else
                        (pred = inorder predecessor of the current node.)
                        pred = current.left
                        while(pred.right != NULL and pred.right != current)
                            pred = pred.right
                        If pred.right == NULL
                            visit(current)
                            pred.right = curr
                            current = current->left
                        Else if right child of inorder predecessor == current
                            pred.right = NULL
                            current = current->right
            ```
    -   For Inorder Traversal
        -   ```c++
                current = root.
                While current != NULL:
                    If current.left == NULL:
                        visit (current)
                        current = current->right
                    Else
                        pred = current.left
                        while(pred.right != NULL and pred.right != current)
                            pred = pred.right
                        If pred.right == NULL:
                            pred.right = current
                            current = current->left
                        Else If pred.right == current:
                            pred.right = NULL
                            visit (current)
                            current = current->right
            ```

### 8. Shortest Path(Graphs)

-   **Dijkstra Algorithm**

    -   ```c++
            function Dijkstra(Graph, source):
                create priority queue(min heap) of pair<dist, node> Q, distance array D
                for each vertex v in Graph:
                    D[v] = INFINITY
                D[source] = 0
                add source to Q
                while Q is not empty:
                    u = vertex in Q with smallest distance[u]
                    remove u from Q
                    for each neighbor v of u:
                        If D[u]!=INT_MAX && D[v] > D[u] + weight(u, v)
                            dist[v] = dist[u] + weight(u, v)
                            Insert v into the pq (Even if v is already there)
                return distance[]
        ```
    -   **Note:** if negative cycle exists then Dijkstra algo does not work

-   **BellMan Ford**
    -   It can handle graphs with negative edge weights
    -   ```c++
            void bellmanFord(vector<Edge> &edges, int V, int source) {
                vector<int> distance(V, INT_MAX);
                distance[source] = 0;
                // Relax all edges V-1 times
                for (int i = 0; i < V - 1; ++i) {
                    for (const auto &edge : edges) {
                        int u = edge.source;
                        int v = edge.destination;
                        int w = edge.weight;
                        if (distance[u] != INT_MAX && distance[u] + w < distance[v]) {
                            distance[v] = distance[u] + w;
                        }
                    }
                }
                // Check for negative-weight cycles
                for (const auto &edge : edges) {
                    int u = edge.source;
                    int v = edge.destination;
                    int w = edge.weight;
                    if (distance[u] != INT_MAX && distance[u] + w < distance[v]) {
                        cout << "Graph contains negative weight cycle" << endl;
                        return;
                    }
                }
                // Print the distances from source
                cout << "Vertex Distance from Source:" << endl;
                for (int i = 0; i < V; ++i) {
                    cout << i << "\t\t" << distance[i] << endl;
                }
            }
        ```

### 9. MST

-   The minimum spanning tree of a graph is a subset of the edges that connects all the vertices together without any cycles and with the minimum possible total edge weight.
-   **Prim Algorithm**
    -   ```c++
            Procedure primMST(graph: matrix of integers[V][V])
                key: array of integers[V] //This array stores the minimum weight of the edge that connects a vertex to the MST
                mstSet: array of booleans[V] //This array is a boolean array that indicates whether a vertex v is included in the MST or not
                parent: array of integers[V] //This array is used to store the parent of each vertex in the MST.
                for i=0; i < V:
                    key[i] := INFINITE
                    mstSet[i] := false
                    parent[i] := -1
                key[0] := 0
                for c = 0; c < V-1:
                    u := minKey(key, mstSet) // minimum key with mstSet = false
                    mstSet[u] := true
                    for v = 0; v< V:
                        if graph[u][v] ≠ 0 and mstSet[v] = false and graph[u][v] < key[v] then
                            parent[v] := u
                            key[v] := graph[u][v]
        ```
-   **Kruskal Algorithm**
    -   ```c++
            // DSU data structure path compression + rank by union
            class DSU {
                parent array of integers
                rank array of integers
                constructor DSU(n):
                    allocate memory for parent and rank arrays of size n
                    for i from 0 to n-1:
                        parent[i] = -1
                        rank[i] = 1
                function find(i):
                    if parent[i] == -1:
                        return i
                    parent[i] = find(parent[i]) // Path compression
                    return parent[i]
                function unite(x, y):
                    s1 = find(x)
                    s2 = find(y)
                    if s1 ≠ s2:
                        if rank[s1] < rank[s2]:
                            parent[s1] = s2
                        else if rank[s1] > rank[s2]:
                            parent[s2] = s1
                        else:
                            parent[s2] = s1
                            rank[s1] += 1
            };
            function kruskals_mst(){
                sort edgelist in non-decreasing order based on the first element (weight)
                create a new DSU object with V vertices
                initialize ans to 0 // total weight of minimum spanning tree
                for each edge in edgelist{
                    w = weight of the edge
                    x = first vertex of the edge
                    y = second vertex of the edge
                    if find(x) ≠ find(y){
                        unite x and y in DSU
                        add w to ans
                    }
                }
            }
        ```

### 10. Strongly Connected Components (SCCs)

-   **Tarjan Algorithm**
    -   It is used to find the edges or vertices(vertices are called articulate point) which upon removal will break the graph in 2 or more components
    -   ```c++
            timer = 1
            // Define DFS function
            function DFS(node, parent,visited,graph,disc,low,bridges)
            {
                visited[node] = true
                disc[node] = timer
                low[node] = timer
                timer++
                child = 0;
                for each neighbor n in graph[node]
                {
                    if neighbor == parent
                    {
                            continue // Skip the edge to parent
                    }
                    else if visited[neighbor]
                    {
                        low[node] = min(low[node], disc[neighbor])
                    }
                    else
                    {
                        DFS(neighbor, node,graph,disc,low,bridges)
                        low[node] = min(low[node], low[neighbor])
                        if low[neighbor] > disc[node]
                        {
                            bridgeList.add((neighbor,node)) // Found a bridge
                        }
                        if low[neighbor] >= disc[node] && parent != -1
                        {
                            bridgeList.add((neighbor,node)) // Found an articulation point
                        }
                        child++;
                    }
                }
                if(parent==-1 && child>1){
                    src is an articulate point
                }
            }
            function findBridges(graph){
                // Initialize variables
                n = graph.size()
                vector<int> visited(n,0); //parent node
                vector<int> disc(n,0); // discovery number, the nodeis discovered at what number
                vector<int> low(n,0); // lowest possible discovered point after ignoring the its own path
                bridgeList = []
                src = 0
                parent = -1
                for i in vertices{
                    if(!visited[i])
                    {
                        dfs(src,parent,visited,graph,disc,low,bridgeList)
                    }
                }
                return bridgeList
            }
        ```
-   **Kosaraju Algorithm**
    -   ```c++
            void DFS(int node, const vector<vector<int>>& graph, vector<bool>& visited, stack<int>& stk) {
                visited[node] = true;
                for (int neighbor : graph[node]) {
                    if (!visited[neighbor]) {
                        DFS(neighbor, graph, visited, stk);
                    }
                }
                stk.push(node);
            }
            void DFSReverse(int node, const vector<vector<int>>& reverseGraph, vector<bool>& visited, vector<int>& component, int componentNumber) {
                visited[node] = true;
                component[node] = componentNumber;
                for (int neighbor : reverseGraph[node]) {
                    if (!visited[neighbor]) {
                        DFSReverse(neighbor, reverseGraph, visited, component, componentNumber);
                    }
                }
            }
            vector<vector<int>> kosaraju(const vector<vector<int>>& graph, const vector<vector<int>>& reverseGraph) {
                int n = graph.size();
                vector<bool> visited(n, false);
                stack<int> stk; // it is used to keep track of the vertices in the order of their finishing times
                // First DFS traversal to fill the stack
                for (int node = 0; node < n; ++node) {
                    if (!visited[node]) {
                        DFS(node, graph, visited, stk);
                    }
                }
                Graph gr = getTranspose();
                // Reset visited array
                fill(visited.begin(), visited.end(), false);
                vector<int> component(n, -1);
                int componentNumber = 0;
                // Second DFS traversal on reverse graph to find SCCs
                while (!stk.empty()) {
                    int node = stk.top();
                    stk.pop();
                    if (!visited[node]) {
                        vector<int> SCC;
                        DFSReverse(node, reverseGraph, visited, component, componentNumber);
                        componentNumber++;
                    }
                }
                // Construct SCCs from components
                vector<vector<int>> SCCs(componentNumber);
                for (int i = 0; i < n; ++i) {
                    SCCs[component[i]].push_back(i);
                }
                return SCCs;
            }
        ```

### 11. Graph Traversal

-   **Depth First Search (DFS)**
    -   ```c++
            function DFS(graph, start_vertex):
            stack<vertex> stack
            set<vertex> visited
            stack.push(start_vertex)
            while stack is not empty:
                current_vertex = stack.pop()
                visited.insert(current_vertex)
                for neighbor in graph.adjacent(current_vertex):
                    if neighbor is not in visited:
                        stack.push(neighbor)
        ```
-   **Breadth-First Search**
    -   ```c++
            function BFS(graph, start_vertex):
                queue<vertex> queue
                set<vertex> visited
                queue.enqueue(start_vertex)
                while queue is not empty:
                    current_vertex = queue.dequeue()
                    visited.insert(current_vertex)
                    for neighbor in graph.adjacent(current_vertex):
                        if neighbor is not in visited:
                            queue.enqueue(neighbor)
        ```

### 12. C++ STL

-   ```c++
    bool comparator(dt v1, dt v2){
        // sorting conditions
    }
    sort(beginIterator, endIterator, comparator); //Sorts in any given order (if comparator not defined asc by default)

    next_permutation(s.begin(),s.end()); // it finds the next permutation of the string in dictonary manner
    ```
