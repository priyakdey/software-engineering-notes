# Radix Sort

**Radix Sort** is a value-based, non-comparative sorting algorithm that sorts integers (or strings) by processing individual digits, starting from the **least significant digit (LSD)** to the **most significant digit (MSD)**.

It works especially well when sorting numbers that are bounded in digit length — for example, integers within a range where the number of digits (`d`) is small.

Radix Sort uses [**Counting Sort as a stable subroutine**](./counting-sort.md) at each digit level.

## Steps
- **Find the maximum element** in the array to determine the number of digits `d`
- For each digit position `place = 1, 10, 100, ...` up to `max_digit_place`:
	- **Apply Counting Sort** using the digit at the current `place` (e.g., units, tens, hundreds).
	- Counting Sort extracts digits using: `(number / place) % 10`
	- Ensure **stability** by iterating the original array **in reverse order** during placement.
- At the end of all digit-level sorts, the array is fully sorted.

## Example
The example in [RadixSort.java](https://github.com/priyakdey/data-structures-algorithms-probe/blob/main/src/main/java/com/priyakdey/probe/dsa/sorting/RadixSort.java) shows an implementation of the algorithm. Though the example takes into account only `Integer` array, but since counting sort is value based, it can sort any Objects, which can be mapped to a numeric value.

## Complexity
Let:

- `n` = number of elements
- `d` = number of digits in the maximum element
- `b` = base (usually 10 for decimal digits)
### Time Complexity
`O(n * d)`  
Since for each of the `d` digit places, we perform Counting Sort in `O(n)` time.
### Space
`O(n + b)`  
We use a temporary output array of size `n` and a frequency array of size `b` (usually 10).

## References
- [CLRS 8.3](https://enos.itcollege.ee/~japoia/algorithms/GT/Introduction_to_algorithms-3rd%20Edition.pdf)
- [Programiz](https://www.programiz.com/dsa/radix-sort)
- [Wikipedia](https://en.wikipedia.org/wiki/Radix_sort)