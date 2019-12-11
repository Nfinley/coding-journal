# Algorithms

## Sorting Algorithms

[References](https://blog.bitsrc.io/a-guide-to-sorting-algorithms-in-javascript-5b32da4eae1e)

### Bubble Sort

- About: Bubble Sort is the simplest sorting algorithm that works by repeatedly swapping the adjacent elements if they are in wrong order.
  - Although the algorithm is simple, it is too slow and impractical for most problems even when compared to insertion sort.Bubble sort can be practical if the input is in mostly sorted order with some out-of-order elements nearly in position.
- Big O Complexity:
  - Space complexity is O(1), because only a single additional memory space is required i.e. for temp variable.
  - Time complexity, it has a worst-case and average complexity of О(n^2), where n is number of items being sorted
  - When the list is already sorted (best-case), the complexity of bubble sort is only O(n)

```javascript
// Bubble sort

function bubblesort(array) {
  let isSorting = false;
  do {
    isSorting = false;
    array.forEach((item, i) => {
      if (item > array[i + 1]) {
        // take out current item and place in temp array
        let temp = item;
        // move next index to left
        array[i] = array[i + 1];
        // put back higher item
        array[i + 1] = temp;
        isSorting = true;
      }
    });
  } while (isSorting);

  return array;
}
```

![Bubble Sort](http://res.cloudinary.com/thefinleycode/image/fetch/https://res.cloudinary.com/thefinleycode/image/upload/v1574993087/Bubble-sort-example-300px_ry8ama.gif)

- [Wiki Reference](https://en.wikipedia.org/wiki/Bubble_sort)

#### Code example

### Insertion Sort
