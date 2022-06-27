# Data Structures

## Primitives

* String
* Number
* BigInt
* Boolean
* Symbol
* null
* undefined
* everything else inherits from Object prototype aka hash tables (key-value pairs)
* **function is a callable object**


## Stack

* list
* LIFO only - the last added element is the first one to come out
* can't access out of order
* examples
	* JS Call stack
	* undo/redo
* BigO
	* insertion - O(1)
	* removal - O(1)
	* searching - O(n) (you would search element by element using the `next` ref)
	* access - O(n)

**Version 1** - array with only push and pop methods

**Version 2** - custom list class with nodes that hav ref to next node. push & pop methods.


### Queue

* similar as Stack but FIFO - first element added is the first one to come out
* examples
	* background tasks - need to be executed one after another in the order sent in
	* printing/task processing
* BigO
	* insertion - O(1)
	* removal - O(1)
	* searching - O(n)
	* access - O(n)


**Version 1** - array with only push and shift methods

**Version 2** - custom list class with `enqueue` and `dequeue` methods


### Linked list

* list, singly or doubly linked list
* each node in the list has one or two pointers to the next or next and previous nodes
* first element is `head`
* last element is `tail`
* don't have indexes like with arrays. each node only knows the nodes it is connected to.
* can't access values randomly
* insertion/deletion is more efficient than with arrays by just having to redirect the pointer of the neighbour node(s) while in arrays values need to be re-indexed
* common methods: `push`, `pop`, `unshift`, `shift`, `get`, `set`, `insert`, `remove`, `reverse`
* BigO
	* insertion - O(1)
	* removal - O(n)
	* search - O(n)
	* access - O(n)
* Doubly linked lists perform better with certain methods but at a cost of consuming more memory
* BigO of doubly
	* insertion - O(1)
	* removal - O(1)
	* search - O(n)
	* access - O(n)


### Tree

* link nodes in a parent/child relationship
* start with a `root` node
* all other nodes are its `children`
* nodes without descendants are `leaves`
* height is determined by the nr of parent/child connections
* non-linear - when iterating, program can follow different directions
* only valid connections is parent->child, not between siblings
* only one root
* examples
	* DOM model
	* situation analysis in AI
	* directory structure
* bigO is O(log n) but only for a balanced tree - means don't have to look through every element, can discard many at once
* log(n) means time goes up linearlly while dataset size goes up exponentially e.g 1s for 10 elems, 2s for 100 elems, etc 


#### Binary tree

* each node has a max of two children
* really useful for searching - Binary Search Tree (BST) is used
* in BST each node that descends to the left of the parent, must have a smaller value than the parent and to the right, a bigger value. this way, lots of data can be discarded in a binary search.


#### Heap

* tree with specific rules
* MaxHeaps - parent nodes always bigger than children
* MinHeaps - parent nodes always smaller than children
* no rules amongst siblings, just that they are smaller/bigger than parent
* as compact as possible
* new nodes put to the left spaces first
* heaps, esp Binary Heaps, are used for for Priority Queues - each elem has a priority and highest priority elems are presented first


### Graph

* group of nodes with certain connections between them
* do not have a root, leaf nodes, hear or tail
* no implicit parent-child relationship
* examples
	* social networks
	* geolocalization
	* recommendation systems
* Undirected Graph - no implicit directions in the connection between nodes
* Directed Graph - clear direction between nodes
* Weighted Graph - if connections between nodes have a weight assigned e.g about time of travel from A to B using different routes
* Unweighted Graph - without weights
* ways to represent in code:
	*  Adjacency matrix - a 2-dimensional array where each row and column represents a node and values 0 or 1 represents connections between nodes
	*  more efficient for querying for specific connections cause know the exact position to look at
	*  need to add new row and column to add a node
	*  Adjacency list - an object where keys are node values and values are arrays listing connected nodes values
	*  more efficient for adding/removing nodes cause need to add a new key and new values to only the connected keys array
	*  to search, need to iterate over the array