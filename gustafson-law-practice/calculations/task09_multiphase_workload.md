# Task 09: Multi-Phase Parallel Workload

## 1. Given Information

A parallel workload consists of three phases:

- Disk I/O and broadcast: 2%
- Boundary synchronization: 6%
- Flux computation: 92%

The number of processors is:
- P = 512
- P = 2048

## 2. Aggregate Serial Fraction

The serial fraction is the sum of the disk I/O/broadcast and boundary synchronization phases.

\[
\alpha = 0.02 + 0.06
\]

\[
\boxed{\alpha = 0.08 = 8\%}
\]

The parallel fraction is:

\[
p = 1 - \alpha = 1 - 0.08 = 0.92
\]

Therefore, 8% of the workload is considered serial and 92% is parallel.

## 3. Gustafson's Law

The scaled speedup formula is:

\[
S(P) = P - \alpha(P-1)
\]

### Case 1: P = 512

\[
S(512) = 512 - 0.08(512-1)
\]

\[
S(512) = 512 - 0.08(511)
\]

\[
S(512) = 512 - 40.88
\]

\[
\boxed{S(512) = 471.12}
\]

### Case 2: P = 2048

\[
S(2048) = 2048 - 0.08(2048-1)
\]

\[
S(2048) = 2048 - 0.08(2047)
\]

\[
S(2048) = 2048 - 163.76
\]

\[
\boxed{S(2048) = 1884.24}
\]

## 4. Results

| Number of Processors | Serial Fraction | Gustafson Speedup |
|---:|---:|---:|
| 512 | 8% | 471.12 |
| 2048 | 8% | 1884.24 |

## 5. Conclusion

The aggregate serial fraction of the workload is 8%. According to Gustafson's Law, increasing the number of processors from 512 to 2048 increases the scaled speedup from 471.12 to 1884.24.

This demonstrates that parallel performance can improve significantly when the workload is scaled with the number of processors. However, communication and synchronization overhead still limit the overall speedup.