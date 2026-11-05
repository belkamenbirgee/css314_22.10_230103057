# Task 11: Sun–Ni Memory-Bounded Speedup Comparison

## 1. Introduction

Amdahl's Law, Gustafson's Law, and the Sun–Ni Memory-Bounded Speedup model describe parallel performance under different conditions.

Amdahl's Law assumes a fixed problem size. Gustafson's Law assumes that the problem size increases with the number of processors. The Sun–Ni model considers how the problem size grows according to the available memory capacity.

Sun and Ni introduced the memory-bounded speedup model to provide a more general framework for analyzing scalable parallel workloads.

## 2. Gustafson's Law

Gustafson's scaled speedup is:

\[
S_G(P)=P-\alpha(P-1)
\]

Where:
- P is the number of processors.
- α is the serial fraction.
- The workload increases with processor count.

The model assumes that the parallel workload grows proportionally with P.

## 3. Sun–Ni Memory-Bounded Speedup

The simplified Sun–Ni model is:

\[
S_{MB}(P)=
\frac{(1-\alpha)+\alpha G(P)}
{(1-\alpha)+\frac{\alpha G(P)}{P}}
\]

Where:
- α is the serial fraction.
- P is the number of processors.
- G(P) is the workload growth factor determined by available memory.

The function G(P) represents how much the parallel workload grows when memory capacity increases.

The model considers the relationship between memory capacity and workload size rather than assuming that workload always grows linearly with processor count.

## 4. Comparison of the Models

| Model | Problem Size Assumption | Main Limitation |
|---|---|---|
| Amdahl's Law | Fixed problem size | Limited by serial fraction |
| Gustafson's Law | Problem size grows linearly with P | Assumes ideal workload scaling |
| Sun–Ni Model | Problem size grows according to memory capacity | Depends on memory-workload relationship |

### Special Cases

The Sun–Ni model can represent both Amdahl's Law and Gustafson's Law.

**Case 1: Fixed workload**

If:

\[
G(P)=1
\]

Then:

\[
S_{MB}(P)=\frac{1}{(1-\alpha)+\alpha/P}
\]

This is Amdahl's Law.

**Case 2: Linear workload growth**

If:

\[
G(P)=P
\]

Then:

\[
S_{MB}(P)=
\frac{(1-\alpha)+\alpha P}
{(1-\alpha)+\alpha}
\]

Since the denominator equals 1:

\[
S_{MB}(P)=(1-\alpha)+\alpha P
\]

This is equivalent to Gustafson's Law:

\[
S_G(P)=P-\alpha(P-1)
\]

Therefore, the Sun–Ni model generalizes both models.

## 5. When Gustafson's Law Overestimates Throughput

Gustafson's Law may overestimate achievable throughput when:

- Memory capacity does not increase enough to support linear workload growth.
- Communication overhead increases with processor count.
- Data replication consumes additional memory.
- Synchronization becomes more expensive.
- Workload distribution becomes unbalanced.

In these situations, the actual workload growth factor G(P) may be smaller than P.

## 6. When Gustafson's Law Underestimates Throughput

Gustafson's Law may underestimate achievable throughput when the workload grows faster than linearly with memory capacity and the parallel system can efficiently process that increased workload.

For example, certain memory-intensive applications may benefit from larger datasets and improved data locality.

However, this result is conditional. Superlinear speedup is not guaranteed and depends on algorithm behavior, cache effects, memory bandwidth, and communication costs.

## 7. Critical Analysis

Gustafson's Law is useful for understanding weak scaling because it assumes that larger parallel systems can solve larger problems within approximately the same execution time.

However, real systems are constrained by memory capacity, communication, synchronization, and workload distribution.

The Sun–Ni model is more general because it incorporates the relationship between memory growth and workload growth. It can describe fixed-size workloads, linearly scaled workloads, and other memory-dependent workloads.

Thus, Gustafson's Law is a useful idealized model, while the Sun–Ni model provides a more flexible framework for analyzing practical parallel systems.

## 8. Conclusion

The Sun–Ni Memory-Bounded Speedup model extends Amdahl's Law and Gustafson's Law by considering memory capacity as a limitation on problem scalability.

Gustafson's Law assumes linear workload growth with processor count, while Sun–Ni allows workload growth to depend on available memory.

The Sun–Ni model is therefore more general and can provide a more realistic understanding of parallel throughput when memory capacity and communication overhead affect performance.

## Reference

Sun, X.-H., & Ni, L. M. (1993). Scalable Problems and Memory-Bounded Speedup. *Journal of Parallel and Distributed Computing, 19*(1), 27–37. https://doi.org/10.1006/jpdc.1993.1087