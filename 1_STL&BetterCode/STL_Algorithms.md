# STL Algorithms

- raising the level of abstraction.
- avoids common mistakes.
    - empty loops iterations (**UB**)
    - out of bound for loops (**UB**)
    - naive Complexity
- Used By lot of people
    - A common vocabulary
    - better then implementing yourself
    - irrelevant to your compiler

## Province of Heap 
Heap is a data structure that have the parent data that is bigger and node that is smaller at the bottom called child. can have many levels. We use heap because we can access the max of the data easily.

### Algorithms on heap

- Make heap from a data structure that has begin and end (**iterator**)
```cpp 
    std::make_heap(begin(a),end(a));
```

- Add number to heap. Not easy because we have to push the number added to the end to the parent number till we can't as parent > child.

```cpp 
    std::push_heap(begin(a),end(a));
```
- similarly we can remove the biggest element from the heap.

```cpp 
    std::pop_heap(begin(a),end(a)); // move the first element to the last and make the iterator based data structure a heap again
    std::pop_back(begin(a),end(a)); // remove the last element, first element of heap in this case.
```

- We can omit the `pop_back()` and just use `std::pop_heap()` to sort the heap. same thing is achieved by the `sort_heap`
```cpp 
    std::sort_heap(begin(a),end(a));
```

## Shores of sorting

- to sort any sortable STL container.
```cpp 
    std::sort(begin(a),end(a));
```

- To sort beginning of the container.
```cpp 
    std::partial_sort(begin(a),end(a), x); //sort till x
```
- sorts the position of the single element and leaves everything below unordered but less and above unordered but higher
```cpp 
    std::nth_element(begin(a),end(a), x); //sort x
```
- sort two merged sorted container
```cpp 
    std::inplace_merge(begin(a),middle , end(a)); // middle is the boundary of the containers
```

## Region of Partitioning

Partition is parting the same data structure towards the one side. for ex. binary 0 and 1. 

- partition with p as binary check, true first, false last.
```cpp 
    std::partition(begin(a),end(a), p);
```
- to return the boundary of partition:
```cpp 
    std::partition_point(begin(a),end(a), x); //sort x
```
## Other Permutation

- move element last to first
```cpp 
    std::rotate(begin(a),middle(a), end(a)); // middle is the first element of the new container.
``` 

- random move
```cpp 
    std::shuffle(begin(a),middle(a)); 
``` 
- reverses the container
```cpp 
    std::reverse(begin(a),middle(a)); 
``` 

## Secret Ruins

- Stable_* - preserve the order
    - `stable_sort()`
    - `stable_partition()`

- is_* - return boolean if true
    - `is_sorted()`
    - `is_partitioned()`
    - `is_heap()`

- is_*_until - returns the position when the condition is not true
    - `is_sorted_until()`
    - `is_partitioned_until()`
    - `is_heap_until()`

## Lands of Queries

- `count()` - gets the count of the element occurs in the dataset.
-  to add elements or to do any binary operations on the container we can use :
```cpp
accumulate(begin, end, initial_sum, Binary_func )
reduce(begin, end, initial_sum, Binary_func ) // this allows parallelization
```
- there is also `transform_reduce()` that applies function before  accumulate
- `partial sum` sums the elements but preserve the last, ex: `sum n = ... + n-2 + n-1 + nth`
    - `inclusive_scan` - runs in parallel
    - `exclusive_scan` - does not include the last element ex: `sum n = ... + n-2 + n-1`
    - both have transform variants - `transform_inclusive_scan()`, `transform_exclusive_scan()`, applies function before the operation.
- `inner_product()` 
- `adjacent_difference()` - gives the difference of the two adjacent elements 
- `sample(n)` - generate collection with n elements selected randomly.

- `all_of()` - returns true if all elements satisfy the conditional
- `any_of()` - returns true if any one elements satisfy the conditional
- `none_of()` - returns true if none elements satisfy the conditional
- `equal()` - returns true if all elements matches and equal in size the conditional
- `lexicographical_compare()` - returns true if first one is smaller as in dictionary 
- `mismatch()` - returns pair of iterator where first mismatch is encountered
- unsorted collection-
    - `find()` - returns position of first occurrence of the searched value.
    - `adjacent_find()` - returns position first occurrence of the first searched value of two adjacent equal value.
    - 




