# Sorting Algorithms
![](img/Sorting+Algorithm.svg)


## Selection Sort
- Running time is insensitive to input
- Data movement is minimal (compare with bubble sort): the number of array access is a linear function of the array size
- Unstable


## Priority Queue & Heapsort
### Priority Queue
- **Unordered array representation**
  - Selecton sort
- **Ordered array representation**
  - Insertion sort
- **Binary heap representation**
  - Heapsort
  - Heap-ordered: each node is larger than or equal to its two children
    - Largest key is at the 
    - The first entry ([0]) is empty
    
   
### Heapsort
- Breaks into 2 phases: `heap construction` and `sortdown`
- Unstable

## Insertion Sort => inserting elements
- Running time depends on the initial order of items in the input
- Efficient for partially sorted arrays
- Fine method for tiny arrays, better than quicksort
- Stable

## Shellsort
- A simple extension of insertion sort  
  - allowing exchanges of array entries that are far apart :arrow_right: produce partially sorted array :arrow_right: do insertion sort :arrow_right: gain speed
- Increment sequence
- Performs well on arrays in arbitrary order
- Useful for large arrays
- Unstable

## Bubble Sort

### Cocktail Shaker Sort

## Quicksort
- Divide-and-conquer
- Shuffle and rearrange the array: put the partitioning item into its final position :arrow_right: `recursive calls`: finish the sort
- Uses few compares: the efficiency of the sort depends on how well the partitioning divides the array
- Requires time propotional to NlogN on average
- In-place, Unstable


## Merge Sort
- Divide-and-conquer
- `Recursive calls`: break into 2 subarrays to be sorted :arrow_right: combine the ordered subarrays
- Guarantees to sort any array of N items in time propotional to NlogN
- Use extra space propotional to N
- Stable

### Top-down mergesort
- Recursive method
### Bottom-up mergesort
- Non-recursive

## Counting Sort

## Bucket Sort => double type

## Radix Sort => string sorts (LSD, MSD)


- In-place: transforms input using no auxiliary data structure  
冒泡排序、选择排序、插入排序、归并排序、快速排序、希尔排序、堆排序  

- Out-of-place: needs extra space to put the elements in as it's sorting them  
计数排序、桶排序、基数排序  

冒泡排序、选择排序、插入排序  
归并排序、快速排序、希尔排序、堆排序  
计数排序、桶排序、基数排序  
