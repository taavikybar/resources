# Algorithms

* stable algorithm - 2 equal items remain in the same order as they were after sorting
* in-place algorithm - transforms input without any auxiliary data structures. small amount of extra storage space is allowed for variables. e.g input is overwritten via swapping or replacing.
* out-of-place algorithm - opposite
* comparison algorithm - only reads a list of elements through a single abstract comparison operation e.g less than, equal to


## Greedy Algorithm

*  attempts to find the solution in small steps locally hoping to find a solution that can be applied globally
*  often greedy algorithms will give the most optimal solution by making the decision that looks best atm. this isn't always the case in real world
*  kind of like bottom up approach


----


## Search algorithms

### Linear search

* e.g `indexOf()`, `includes()`, `find()`, `findIndex()`
* simply loops over every element
* time complexity O(1) to O(n) depending on the location of the element
* space complexity O(1) cause its in-place
* best possible option for **unsorted arrays**


### Binary search

* better for sorted arrays
* O(1) to O(log n) - divide&conquer, much more performant for large arrays
* start in the middle, check if target is smaller or greater, choose appropriate half, repeat until value found
* in-place, space complexity O(1)


### Breadth First Search

* looks at all the nodes at a given depth before moving further in depth


### Depth First Search

* 

----

## Sorting algorithms

* usually sorting order is lexicographical e.g alphabetical or numerical

### Bubble sort

* loops through an array and compares 2 elements. swaps them if needed. repeats until sorted.
* min 2 runs needed - 1st to sort, 2nd to check, resulting O(n) complexity
* worst case if array is in reverse order - O(n^2) quadric time complexity
* space complexity O(1) cause in-space using 2 additional memory spaces for the loop variables i and j
* usually don't use. instead use better alternatives
* stable, comparison sort

### Selection sort

* goes through the array and looks for the minimum value. moves that to the beginning of the array.
* the left side of the array becomes more and more sorted with each pass meaning the right side that needs to be iterated over decreases and the smallest element from the right side is moved to the end of the left side
* O(n^2) for best and worst case scenario
* unstable, comparison sort
* can outperform on small arrays but Insertion sort can be better

### Insertion sort

* compares element to elements to the left until a smaller element is found. moves it in front of the current element.
* best case O(n), worst case O(n^2) if in reverse order
* can be used as "live/online algorithm" meaning data is sorted as given, don't need the whole dataset to be available. because left oriented sorting.
* good for small and almost sorted arrays. not good for larger.
* in-space, stable, comparison sort


### Merge sort

* one of the most efficient. divide&conquer.
* divides the array into 0 or 1 length arrays. these are merged together to bigger arrays that are sorted. the larger arrays elements are compared with elements from other large arrays, merging them together.
* constant O(n * log(n)) linearithmic time complexity. log(n) from divisions and O(n) from comparisons needed to make to merge the arrays back together.
* due to needing to store the merged arrays in memory, has space complexity of O(n)
* fast with the expense of using up space. usually time is bigger consideration.
* out-of-place, stable, comparison sort


### Quick sort

* select a pivot, usually 1st element. go over all the elements and move them to the left or right of the pivot depending on whether they are smaller or bigger. this way the pivot will be in the right place.
* for each side, choose a new pivot, move elements accordingly, the pivot will be in the right place.
* best case O(n*log(n)) linearithmic time complexity. log(n) from decompositions to subarrays, O(n) from comparisons in the subarrays.
* worst case O(n^2)
* space complexity O(log(n))
* in-place, unstable, comparison sort
* good at large arrays but Insertion Sort better at smaller


### Radix sort

* sorts without making any comparisons between elements
* creates buckets 0-9. looks at the rightmost digit of each number, sorts into buckets by that. puts them back into an array by this new order.
* repeats by the 2nd rightmost digit until the number with the longest digits is sorted.
* time complexity depends on the nr of digits in the longest number, k, O(k*n)
* space complexity is O(n+d) where d is the amount of values each digit could be, e.g 10 for 0-9. space is taken up by the buckets created.
* can outperform Merge and Quick sorts in some cases.
* not that popular cause needs tweeking if working with non-ints
* out-of-place, unstable, non-comparison sort

### Comparison table

![](https://www.doabledanny.com/static/ba421c56ffca52e8c24c8e5429bb8785/93d59/15.jpg)











