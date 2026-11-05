# Task 01: Strong Scaling vs. Weak Scaling Foundations

## 1. Introduction

Amdahl's Law and Gustafson's Law are two fundamental models used to analyze parallel computing performance. Both laws describe the relationship between the number of processors and speedup, but they use different assumptions about problem size and execution time.

Amdahl's Law focuses on strong scaling, while Gustafson's Law focuses on weak scaling.

## 2. Amdahl's Law (1967)

Amdahl's Law assumes that the total problem size remains constant while the number of processors increases.

The speedup formula is:

\[
S_A(P)=\frac{1}{s+\frac{1-s}{P}}
\]

Here, \(P\) is the number of processors, \(s\) is the serial fraction, and \(1-s\) is the parallel fraction.

The serial portion cannot be divided among multiple processors. Therefore, it limits the maximum achievable speedup.

As the number of processors approaches infinity:

\[
\lim_{P\to\infty}S_A(P)=\frac{1}{s}
\]

The problem dimension remains fixed because the total workload does not change.

This model is called fixed-size or strong scaling because the same problem is distributed across an increasing number of processors to reduce execution time.

## 3. Gustafson's Law (1988)

Gustafson's Law assumes that the problem size increases with the number of processors while the parallel execution time remains approximately constant.

The scaled speedup formula is:

\[
S_G(P)=P-\alpha(P-1)
\]

Here, \(P\) represents the number of processors, \(\alpha\) is the serial fraction measured on the parallel system, and \(1-\alpha\) is the parallel fraction.

The formula can be expanded:

\[
S_G(P)=P(1-\alpha)+\alpha
\]

As \(P\) approaches infinity:

\[
\lim_{P\to\infty}S_G(P)=\infty
\]

provided that \(\alpha<1\).

In this model, the problem dimension increases as the number of processors grows. More processors allow a larger workload to be completed in approximately the same time.

This is called fixed-time or weak scaling.

## 4. Comparison

Amdahl's Law assumes a fixed total workload and attempts to minimize execution time. Its speedup is limited by the serial fraction.

Gustafson's Law assumes that the workload grows with the number of processors. It focuses on increasing computational capacity while maintaining approximately constant execution time.

The main difference is that Amdahl's Law studies how quickly the same problem can be solved, whereas Gustafson's Law studies how much larger a problem can be solved in the same amount of time.

## 5. Conclusion

Amdahl's Law is useful for analyzing fixed-size workloads, such as processing a constant dataset. Gustafson's Law is more suitable for large scientific simulations and other applications where the workload can grow with available computing resources.

Both laws are important because they provide different perspectives on parallel performance. Amdahl's Law emphasizes the limitations caused by serial execution, while Gustafson's Law demonstrates the potential benefits of scaling the problem size.

