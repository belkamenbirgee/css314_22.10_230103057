# Task 17: 3D Stencil Hydrodynamics Simulation

## 1. Introduction

A 3D stencil solver is used in scientific simulations such as fluid dynamics and heat transfer.

The simulation operates on a cubic grid with dimensions:

\[
N\times N\times N
\]

Each interior grid point is updated using its neighboring points. In a 7-point stencil, each update uses the center point and its six direct neighbors.

## 2. Computational Complexity

The number of grid points is:

\[
V=N^3
\]

Therefore, the computational workload is:

\[
W_{compute}=O(N^3)
\]

Boundary communication occurs across the six faces of the cube. The total surface area is proportional to:

\[
A=6N^2
\]

Thus, communication overhead is:

\[
W_{communication}=O(N^2)
\]

## 3. Communication-to-Computation Ratio

The ratio is:

\[
R=\frac{W_{communication}}{W_{compute}}
\]

Substituting the complexity expressions:

\[
R=\frac{N^2}{N^3}
\]

Therefore:

\[
\boxed{R=\frac{1}{N}}
\]

As the grid dimension increases, the communication-to-computation ratio decreases.

This means larger 3D domains can use processor resources more efficiently because computation grows faster than boundary communication.

## 4. Applying Gustafson's Law

Under weak scaling, the total grid volume grows proportionally with the number of processors:

\[
N^3\propto P
\]

Taking the cube root:

\[
\boxed{N\propto P^{1/3}}
\]

The communication-to-computation ratio becomes:

\[
R(P)\propto\frac{1}{P^{1/3}}
\]

For example:

| Processors (P) | Grid dimension (relative to N=1) | Relative communication ratio |
|---:|---:|---:|
| 1 | 1 | 1.000 |
| 8 | 2 | 0.500 |
| 27 | 3 | 0.333 |
| 64 | 4 | 0.250 |
| 125 | 5 | 0.200 |
| 512 | 8 | 0.125 |

## 5. Analysis

The results show that computation increases with the volume of the grid, while communication increases with its surface area.

When the problem size grows proportionally with processor count, the grid dimension increases as \(P^{1/3}\). Consequently, the communication-to-computation ratio decreases.

However, this ideal result assumes a well-balanced domain decomposition and efficient communication. Real systems can still experience network latency, synchronization delays, and load imbalance.

## 6. Conclusion

For a 3D stencil solver:

- Computation grows as \(O(N^3)\).
- Boundary communication grows as \(O(N^2)\).
- The communication-to-computation ratio decreases as \(1/N\).

Under Gustafson's weak scaling:

\[
\boxed{N\propto P^{1/3}}
\]

Therefore:

\[
\boxed{R(P)\propto P^{-1/3}}
\]

This demonstrates why 3D stencil simulations can benefit from weak scaling: increasing the domain size can improve the ratio of useful computation to communication.