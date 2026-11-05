# Task 12: Communication Overhead Penalty Integration

## 1. Introduction

Classic Gustafson's Law assumes that the serial fraction remains constant as the number of processors increases. However, distributed systems require communication between processors. Communication overhead can increase with the number of processors and reduce the overall speedup.

The classic Gustafson's Law is:

\[
S_G(P)=P-\alpha(P-1)
\]

where:
- \(P\) is the number of processors.
- \(\alpha\) is the serial fraction of the workload.
- \(1-\alpha\) is the parallel fraction.

## 2. Modified Gustafson's Law

To include communication overhead, we introduce a communication penalty term \(C(P)\):

\[
\boxed{S_{modified}(P)=P-\alpha(P-1)-C(P)}
\]

Here, \(C(P)\) represents the additional speedup penalty caused by communication between processors.

Communication overhead can grow in different ways depending on the system architecture.

### Logarithmic communication overhead

For systems where communication grows approximately logarithmically:

\[
C(P)=\beta\log_2(P)
\]

The modified model becomes:

\[
\boxed{S_{modified}(P)=P-\alpha(P-1)-\beta\log_2(P)}
\]

where \(\beta\) is a communication cost coefficient.

### Square-root communication overhead

For systems where communication grows approximately with the square root of the processor count:

\[
C(P)=\beta\sqrt{P}
\]

The model becomes:

\[
\boxed{S_{modified}(P)=P-\alpha(P-1)-\beta\sqrt{P}}
\]

## 3. Example Calculation

Assume:

- Serial fraction: \(\alpha=0.05\)
- Number of processors: \(P=64\)
- Communication coefficient: \(\beta=0.2\)
- Logarithmic communication model

First, calculate the classic Gustafson speedup:

\[
S_G(64)=64-0.05(64-1)
\]

\[
S_G(64)=64-3.15=60.85
\]

Next, calculate communication overhead:

\[
C(64)=0.2\log_2(64)
\]

\[
C(64)=0.2(6)=1.2
\]

Finally, calculate the modified speedup:

\[
S_{modified}(64)=60.85-1.2
\]

\[
\boxed{S_{modified}(64)=59.65}
\]

## 4. Conclusion

The modified Gustafson's Law includes communication overhead that increases with the number of processors. Unlike the classic model, it accounts for the cost of exchanging data between processors.

This model shows that adding processors does not always produce the ideal speedup. Communication overhead can reduce performance, especially in large distributed systems. The communication coefficient must be estimated from the actual system or benchmark results.