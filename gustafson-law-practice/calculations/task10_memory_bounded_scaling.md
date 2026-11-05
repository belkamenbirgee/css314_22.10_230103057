# Task 10: Memory-Bounded Weak Scaling

## 1. Given Information

Each compute node has 32 GB of memory.

The number of nodes:
- Case 1: P = 64 nodes
- Case 2: P = 512 nodes

Assumptions:
- Each grid element uses 8 bytes (double precision).
- The problem is a cubic 3D grid of dimension N × N × N.
- Memory is fully available for the grid.

## 2. Memory Model

The total memory increases linearly with the number of nodes:

\[
M(P) = 32P \text{ GB}
\]

The memory required by the 3D grid is:

\[
M = 8N^3 \text{ bytes}
\]

Therefore:

\[
N^3 = \frac{32P \times 10^9}{8}
\]

\[
N = \sqrt[3]{4 \times 10^9 P}
\]

## 3. Case 1: 64 Nodes

Total memory:

\[
M(64) = 32 \times 64 = 2048 \text{ GB}
\]

Number of grid elements:

\[
N^3 = \frac{2048 \times 10^9}{8}
\]

\[
N^3 = 256 \times 10^9
\]

Grid dimension:

\[
N = \sqrt[3]{256 \times 10^9}
\]

\[
\boxed{N \approx 6349}
\]

The maximum cubic grid dimension is approximately 6349 × 6349 × 6349.

## 4. Case 2: 512 Nodes

Total memory:

\[
M(512) = 32 \times 512 = 16384 \text{ GB}
\]

Number of grid elements:

\[
N^3 = \frac{16384 \times 10^9}{8}
\]

\[
N^3 = 2.048 \times 10^{12}
\]

Grid dimension:

\[
N = \sqrt[3]{2.048 \times 10^{12}}
\]

\[
\boxed{N \approx 12699}
\]

The maximum cubic grid dimension is approximately 12699 × 12699 × 12699.

## 5. Results

| Number of Nodes | Total Memory (GB) | Approximate Grid Dimension N |
|---:|---:|---:|
| 64 | 2048 | 6349 |
| 512 | 16384 | 12699 |

## 6. Conclusion

When the number of nodes increases from 64 to 512, the total memory increases by a factor of 8.

However, the grid dimension N increases by approximately a factor of 2 because the problem is three-dimensional.

This demonstrates weak scaling: the total problem size increases with the number of processors while memory per node remains constant.

The calculation assumes decimal GB and double-precision grid elements. Actual usable grid dimensions may be smaller because of additional memory requirements.