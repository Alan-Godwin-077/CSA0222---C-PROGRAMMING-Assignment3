# Assignment 3 – Searching, Sorting, Merging and Array/String Processing

**Student:** Kabilan P  
**Register Number:** 1911260250  
**Repository:** `CSA02-1911260250-Assignment3`  
**GitHub link:** [ADD AFTER CREATING THE REPOSITORY]

## Submission note
The task folders contain C implementations and captured outputs. The report below provides concise design and complexity notes. Measurements shown by the programs are sample local executions, not claims of large-scale benchmarking. Add your own terminal screenshots and timing tables on your Mac before submission.

## Q1 – Searching a Library Catalogue
Linear search works on unsorted data and takes O(n) worst-case comparisons; binary search requires ascending sorted data and takes O(log n). For 100,000 items, binary search needs at most about 17 comparisons, while linear search may need 100,000. The midpoint expression `low + (high-low)/2` avoids overflow from adding two large indices. A missing key follows a path to an empty interval and therefore can require the maximum search depth.

## Q2 – Sorting
Bubble sort with early exit, selection sort and insertion sort are O(n²) worst case. Bubble and insertion are stable in the usual adjacent-swap/strict-shift implementations; selection sort is generally unstable. Insertion sort is well suited to nearly sorted data because it shifts only out-of-order elements. For 20 late registrations in an otherwise sorted list, insertion sort is a practical choice.

## Q3 – Merging merit lists
The two-pointer merge runs in O(m+n) time and uses O(m+n) extra output space. Each comparison advances at least one input pointer. If one list ends, the remaining suffix of the other list is copied directly. Concatenating and sorting again costs O((m+n) log(m+n)) with a comparison sort.

## Q4 – Rainfall arrays
A 2-D array is stored row-major in C. Address of `rain[i][j]` is base + `(i*columns+j)*sizeof(element)`. Row-wise traversal uses contiguous memory and usually has better cache locality than column-wise traversal. Annual totals, monthly averages and maximum search each take O(rows*columns) time.

## Q5 – String processing
A C string ends at `\0`. A word begins when a non-whitespace character follows the start or whitespace. The palindrome routine skips punctuation and compares letters without regard to case. Each pass is O(n); repeated `strlen` in a loop condition can make a scan O(n²). Recursive reversal uses O(n) stack space, while iterative reversal uses O(1).

## Q6 – Sorting and searching names
`strcmp` compares character codes lexicographically and is case-sensitive. Sorting names costs O(n²) with the included simple sort; binary search after sorting is O(log n) comparisons, each potentially O(L) characters. Sorting indices or pointers reduces character-copying during swaps but requires an auxiliary index/pointer array.

## Q7 – Election counting
A count array indexed by candidate number counts all votes in O(v+c) time and O(c) extra space. Invalid entries are rejected in the same pass. Sorting candidate IDs by their totals costs O(c²) in this compact implementation. Searching candidate names for every vote costs O(v*c); sorting all votes costs O(v log v). Tie detection compares the top counts after ordering.
