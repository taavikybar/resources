# Big O

* considerations around speed and memory consumption of algorithms
* how does the usage of resources scale when data scales
* focuses on the worst case scenario
* n - something to use as a measure e.g nr of elements in an array
* basically, how a many times a piece of code gets executed wit regards to dataset size
* nested loops are poor performance cause O scales in squared
* different big O for time and space consumption. time is usually highest priority.
* if not creating anything into memory then O(1)
* O(1) - if the time is more or less constant even if the data size increases e.g performing 1-2 or so functions. best possible solution. `push()`, `pop()`
* O(log n) - as the data size increases by 2x, the complexity increases by 1. log(base 2)16=4 meaning the complexity will be the power the base (usually 2 in computers) needs to be raised to get the nr of elements in data set. e.g Binary Search algorithm because the data set is halved with each search iteration. 
* O(n) - using up the exact same amount of memory as the dataset (e.g copying values to a new dataset). the algorithm scales 1:1 with the data, linear time complexity. often the best possible scenario. `shift()` `unshift()`
* O(n log n) - combination of linear and logarithmic time. e.g an outer loop that iterates over elements, containing an inner loop that is cutting the data set with each iteration. "worst of the best". e.g Merge Sort - divide&conquer approach
* O(n^2) - e.g nested loops. very poor performance. quadratic time complexity
* O(2^n) - exponential time complexity, nr of operations doubles with every time input is increase by one. opposite of logarithmic time. e.g fibonacci - nr is the sum of 2 previous nr-s. very poor performance.
* O(n!) - factorial time complexity. worst. factorial - is the multiplication of every number up to that number




![](https://www.doabledanny.com/static/31985456f982a6965ee675e767256140/93d59/1.jpg)



