# Counting Sort

**Counting Sort** is a value based, non-comparative sorting algorithm that sorts elements based on the frequency of each unique value.

It assumes that each of the `n` input elements is an integer within a known, finite range `[0...k]`.

## Steps
- **Find the maximum element** in the array to determine the range
- **Create a freq array** `freq[]` of size `max_element + 1`, initialized with `0`
- **Count the frequency** of each element by iterating through the input array.
- Compute the cumulative sum of the frequencies at each index
- **Compute cumulative frequency (prefix sum)** to determine the positions of elements in the sorted array.
- **Build the output array**:
	- Traverse the original array **in reverse order** (important for **stability**).
	- For each element:
		- Use the cumulative count to find its correct index.
		- Place it at `output[freq[element] - 1]`.
		- Decrement `freq[element]`.
## Example
The example in [CountingSort.java](https://github.com/priyakdey/data-structures-algorithms-probe/blob/main/src/main/java/com/priyakdey/probe/dsa/sorting/CountingSort.java) shows an implementation of the algorithm. Though the example takes into account only `Integer` array, but since counting sort is value based, it can sort any Objects, which can be mapped to a numeric value.

## Complexity
Taking into consideration, `n` elements with maximum value as `k`, the complexity is as below:

### Time Complexity
Time complexity is `O(n + k)`, since we have to linearly iterate over the original array, processing each element, and then iterate over the freq array for cumulative sum.
### Space Complexity
The space complexity is also `O(n + k)`, considering, we allocate space for freq, and then another temporary buffer for storing the elements in sorted order.

## References
- [Programiz](https://www.programiz.com/dsa/counting-sort)
- [CLRS](https://enos.itcollege.ee/~japoia/algorithms/GT/Introduction_to_algorithms-3rd%20Edition.pdf)
- [Wikipedia](https://en.wikipedia.org/wiki/Counting_sort)