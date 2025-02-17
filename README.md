# Hidden Performance Pitfalls in std::vector<bool>

This repository demonstrates a common, yet often overlooked, performance issue related to `std::vector<bool>` in C++.  `std::vector<bool>` is specialized to save space by packing boolean values, but this optimization sacrifices the usual contiguous memory layout of other vector types.

This can lead to significantly slower execution times when used with algorithms that assume contiguous data, such as `std::sort` or when interfacing with libraries expecting a contiguous memory block.

The `bug.cpp` file shows example code that highlights the performance problem.  The `bugSolution.cpp` file offers a solution to mitigate this issue.

## How to reproduce

1. Clone the repository.
2. Compile and run `bug.cpp` (observe execution time).
3. Compile and run `bugSolution.cpp` (observe execution time and compare).

## Solution

The preferred solution is usually to avoid `std::vector<bool>` entirely and use a different approach, such as `std::vector<char>` (using a single bit in each byte) or a bitset if space efficiency is paramount. See `bugSolution.cpp` for an example using a bitset.