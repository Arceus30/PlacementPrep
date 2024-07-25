# Algorithms

#### 1. [Recursion (GFG)](https://www.geeksforgeeks.org/cpp-recursion/)

#### 2. Searching

-   **Linear Search**: Search for target one by one
-   **[Binary Search (GFG)](https://www.geeksforgeeks.org/binary-search/)**

#### 3. [Sorting (GFG)](https://www.geeksforgeeks.org/sorting-algorithms/)

-   **Selection Sort:**: It is used when array size is small and there are memory constraints
-   **Bubble Sort**: It is used when there is a need to either find ith largest element or place ith largest element at its right location
-   **Insertion Sort**: This sorting technique is dynamic in nature the array is getting partially sorted as the number of iterations passed
-   **Merge Sort**
-   **Quick Sort**
-   **Heap Sort**
-   **Bucket Sort**
-   **Radix Sort**
-   **Counting Sort**
-   **Sorting Table**
    | Name | Best Case | Average Case | Worst Case | Memory | Stable |
    | -------------- | --------- | ------------ | ---------- | ------ | ------ |
    | Selection Sort | n^2 | n^2 | n^2 | 1 | No |
    | Bubble Sort | n | n^2 | n^2 | 1 | Yes |
    | Insertion Sort | n | n^2 | n^2 | 1 | Yes |
    | Merge Sort | n\*log(n) | n\*log(n) | n\*log(n) | n | Yes |
    | Quick Sort | n\*log(n) | n\*log(n) | n^2 | log(n) | No |
    | Tim Sort | n | n\*log(n) | n\*log(n) | n | Yes |
    | Heap Sort | n\*log(n) | n\*log(n) | n\*log(n) | 1 | No |
    | Tree Sort | n\*log(n) | n\*log(n) | n\*log(n) | n | Yes |
    | Shell Sort | n\*log(n) | n^(4/3) | n^(3/2) | 1 | No |
    | Bucket Sort | n+k | n+k | n^2 | n+k | Yes |
    | Radix Sort | d\*(n+b) | d\*(n+b) | d\*(n+b) | n+b | Yes |
    | Counting Sort | n+k | n+k | n+k | n | Yes |

, where n = number of elements, k = number of buckets, d = number of digits, b = base

-   Stable sorting algorithms preserve the relative ordering of equal elements.
-   Optimal Choices:

    -   For small arrays (2 to 11): Insertion Sort
    -   For medium arrays (60 to 250): STL sort or Quicksort
    -   For large arrays (100k to 200k): Radix Sort

-   **[Topological Sort (Graphs) (GFG)](https://www.geeksforgeeks.org/topological-sorting-indegree-based-solution/?ref=lbp)**

#### 4. BackTracking

-   finding a solution incrementally by trying different options and undoing them if they lead to a dead end.

```cpp
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

#### 5. Dynamic Programming

-   solve complex problems by solving each subproblem only once and storing the results, it avoids redundant computations, leading to more efficient solutions for a wide range of problems.

#### 6. [Floyd's Cycle Detection Algo (GFG)](https://www.geeksforgeeks.org/floyds-cycle-finding-algorithm/)

#### 7. [Traversal (GFG)](https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/)

-   **[Boundary Traversal (GFG)](https://www.geeksforgeeks.org/boundary-traversal-of-binary-tree/)**: left boundary (nodes on left excluding leaf nodes), leaves (consist of only the leaf nodes), right boundary (nodes on right excluding leaf nodes)
-   **[Morris Traversal (GFG)](https://www.geeksforgeeks.org/morris-traversal-for-preorder/)**: traverse the tree without using stack and recursion.

#### 8. Graph Traversal

-   **[Depth First Search (DFS) (GFG)](https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/)**
-   **[Breadth-First Search (GFG)](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/)**

#### 9. Shortest Path(Graphs)

-   **[Dijkstra Algorithm (GFG)](https://www.geeksforgeeks.org/c-program-for-dijkstras-shortest-path-algorithm-greedy-algo-7/)**
-   **[BellMan Ford (GFG)](https://www.geeksforgeeks.org/bellman-ford-algorithm-dp-23/)**: It can handle graphs with negative edge weights

#### 10. MST

-   subset of the edges that connects all the vertices together without any cycles and with the minimum possible total edge weight.
-   **[Prim Algorithm (GFG)](https://www.geeksforgeeks.org/prims-minimum-spanning-tree-mst-greedy-algo-5/)**
-   **[Kruskal Algorithm (GFG)](https://www.geeksforgeeks.org/kruskals-minimum-spanning-tree-using-stl-in-c/)**

#### 11. Strongly Connected Components (SCCs)

-   **[Tarjan Algorithm (GFG)](https://www.geeksforgeeks.org/tarjan-algorithm-find-strongly-connected-components/)**
    -   find the edges or vertices(vertices are called articulate point) which upon removal will break the graph in 2 or more components
-   **[Kosaraju Algorithm (Topcoder)](https://www.topcoder.com/thrive/articles/kosarajus-algorithm-for-strongly-connected-components)**

#### 12. [C++ STL (GFG)](https://www.geeksforgeeks.org/c-magicians-stl-algorithms/)

```c++
next_permutation(s.begin(),s.end()); // it finds the next permutation of the string in dictonary manner
```
