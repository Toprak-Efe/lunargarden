#datastructure #algorithm 
Heap is an adorable data structure that implements the heapsort sorting algorithm, which uses a paradigm different than that o merge sort and insertion sort.

It is essentially an array visualized as a nearly complete binary tree. Below is an array of 10 elements.
# Types of Heap
There are two sub-types of heap which are classified by the order of their terms within the imaginative binary tree.
* Max-Heap is a type of heap whose any element's key is larger than it's children.
* Min-Heap is the exact reverse, where the key of an element is smaller than that of it's children.
# Priority Queue
#priorityqueue
Implements a set $S$ of elements, each of elements is associated with a specific key. Inserting new elements and extracting them runs rather quickly, in the sense of asymptotical time complexity.
## Types of Operations
### insert($S$, $x$)
Insert $x$ element into $S$.
### max($S$)
Return the element of $S$ with the largest key.
### extract_max($S$)
Removes the maximum element from $S$.
### increase_key($S$, $x$, $k$)
Increase the value of $x$'s key to the new value $k$.
### build_max_heap($A$)
Produce a max-heap from an unordered array $A$.
### max_heapify($A$)
Correct a single violation of the heap property in a subtree's root.