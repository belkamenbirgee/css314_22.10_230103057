# Task 16: Dense Matrix Multiplication Scaling (GEMM)

## 1. Introduction

Dense matrix multiplication calculates:

\[
C=A\times B
\]

where A, B, and C are square matrices of dimension \(N\times N\).

The computational complexity is:

\[
W(N)=O(N^3)
\]

The memory requirement is:

\[
M(N)=O(N^2)
\]

Under Gustafson's Law, the workload increases with the number of processors while parallel execution time remains approximately constant.

## 2. Deriving Matrix Dimension Growth

Assume the number of processors is \(P\).

For constant parallel runtime, the total computational workload must grow proportionally with the processor count:

\[
W(N)\propto P
\]

Since matrix multiplication requires \(O(N^3)\) operations:

\[
N^3\propto P
\]

Taking the cube root of both sides:

\[
\boxed{N\propto P^{1/3}}
\]

Therefore, the matrix dimension must grow with the cube root of the number of processors.

## 3. Memory Growth

The memory requirement is proportional to:

\[
M(N)\propto N^2
\]

Substituting the dimension growth formula:

\[
M(P)\propto (P^{1/3})^2
\]

Therefore:

\[
\boxed{M(P)\propto P^{2/3}}
\]

This means that memory requirements grow more slowly than the number of processors.

## 4. Scaling Targets

Assuming the initial matrix dimension is \(N_1=100\) when \(P=1\):

\[
N(P)=100P^{1/3}
\]

| Processors (P) | Matrix dimension (N) | Relative memory |
|---:|---:|---:|
| 1 | 100 | 1× |
| 8 | 200 | 4× |
| 27 | 300 | 9× |
| 64 | 400 | 16× |
| 125 | 500 | 25× |
| 512 | 800 | 64× |
| 1000 | 1000 | 100× |

Relative memory is calculated as:

\[
\frac{M(P)}{M(1)}=P^{2/3}
\]

## 5. Analysis

The results demonstrate that matrix dimension does not need to increase linearly with the processor count.

For example, increasing the number of processors from 1 to 64 allows the matrix dimension to increase from 100 to 400 while maintaining approximately constant parallel execution time under ideal weak scaling.

However, real systems may experience communication overhead, memory bandwidth limitations, and synchronization costs.

## 6. Conclusion

For dense matrix multiplication, computational work grows as \(O(N^3)\), while memory grows as \(O(N^2)\).

Using Gustafson's weak-scaling assumption, the required matrix dimension follows:

\[
\boxed{N(P)=N_1P^{1/3}}
\]

Memory requirements grow as:

\[
\boxed{M(P)\propto P^{2/3}}
\]

This demonstrates how matrix multiplication can scale with additional processors without requiring memory to grow at the same rate as processor count.