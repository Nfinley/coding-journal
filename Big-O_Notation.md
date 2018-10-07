# Big O Notation

### Good Article Links: 
1. [Time/Complexity](https://medium.com/javascript-scene/time-complexity-big-o-notation-1a4310c3ee4b)
2. [CompSci101](https://www.daveperrett.com/articles/2010/12/07/comp-sci-101-big-o-notation/)
3. 



## What is it?
* Big O measures how well an operation will scale when you increase the amount of `things` it operates on
* It can be used to describe how fast an algorithm will run, or it can describe other behaviors like how much memory an algorithm will use

## Types
### O(1) - Contant Time  
* Means that no matter how large the input is the time taken doesn't change
* Examples are:
    * Determining if a number is even or odd
    * Using a constant-size lookup table or hash table


### O(log n) - Logrithimic Time
* Any algorithm that cuts the problem in half each time it runs
* Operations will take longer as the input size increases but once the input gets faily large it won't change enough to worry about
* Example is: 
    * Finding an item in a sorted list with a balanced search tree or binary search

### O(n) - Linear Time
* Means that for every element you are doing a constant number of operations such as comparing each element to a known value
* The larger the input the longer it takes
* Every time you double _n_ the operation will take twice as long
* Example: 
    * Finding an item in an unsorted list
    * Naive string comparison (output == input) is O(n).

### O(n log n) - Loglinear Time
* Means that you are performing an O(log n) operation for each item in your input. Most (efficient) sort algorithms are examples of this
* Increasing the input size hurts, everytime you double the _n_ you spend twice as much time plus a little more
* Examples: 
    * Quicksort - in average and best case
    * Heapsort
    * Merge sort
  
### O(n^2) - Quadratic Time
* Means that for every element you do something with every other element like comparing them
* Really only practical up to a certain input size
* Every time _n_ doubles, the operation takes 4 times as long
* Examples of O(n^2): 
    * Quicksort
    * Bubblesort

### O(2^n)- Exponential Time
* Means time take will double each additional element in the input data set
* The operation is impractical for any reasonably large input size
* Example: 
    * Traveling Salesman problem (using dynamic programming)

### O(n!) - Factorial Time
* Means doing something for all possible permutations of the _n_ elements
* Impractical for any reasonably large input size
* Example: 
    * Traveling Salesman problem (using brute force) where every combination of paths will be examined

### Amortized Analysis
* Some operations run in amortized time meaning: if you do an operation a millino time you don't really case about worst-case and best-case, what you care about is how much time is taken in total when you repeat the operation a million times


buble = O(n^2)
factorial = factorial
bob = O(1) - constant
palindrome = O(n)
sum = O(n)
is prime = O(n)
word = O(n)