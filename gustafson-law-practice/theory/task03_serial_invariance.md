# Task 03: The Serial Fraction Invariance Paradox

## 1. Introduction

Amdahl's Law and Gustafson's Law use different reference systems to measure the serial fraction of a program. This difference explains the apparent contradiction between limited speedup and massive parallel scaling.

In Amdahl's Law, the serial fraction \(s\) is measured on a single processor. In Gustafson-Barsis's Law, the serial fraction \(\alpha\) is measured on the parallel machine.

## 2. Serial Fraction in Amdahl's Law

Amdahl's Law assumes a fixed problem size. The serial fraction is measured on a uniprocessor system.

The speedup formula is:

\[
S_A(P)=\frac{1}{s+\frac{1-s}{P}}
\]

As the number of processors approaches infinity:

\[
\lim_{P\to\infty}S_A(P)=\frac{1}{s}
\]

This means that the serial fraction creates a theoretical upper limit on speedup.

For example, if \(s=0.01\), the maximum speedup is:

\[
S_{\max}=\frac{1}{0.01}=100
\]

## 3. Serial Fraction in Gustafson's Law

Gustafson's Law measures the serial fraction on the parallel machine during execution.

The scaled speedup formula is:

\[
S_G(P)=P-\alpha(P-1)
\]

Here, \(\alpha\) represents the serial fraction of the parallel execution time.

The equivalent serial workload is determined by multiplying the parallel portion by the number of processors while retaining the serial portion.

Therefore:

\[
S_G(P)=\alpha+(1-\alpha)P
\]

This formula allows the workload to increase with the processor count while maintaining approximately constant parallel execution time.

## 4. Resolving the Apparent Contradiction

The apparent contradiction occurs because the two laws measure performance under different assumptions.

Amdahl's Law uses a fixed problem size and a serial fraction measured on a single processor. Its serial fraction limits the speedup because the workload cannot expand.

Gustafson's Law uses a scaled problem size and measures the serial fraction on the parallel machine. The parallel workload can increase with the number of processors, so the serial fraction does not necessarily impose the same fixed upper limit.

The two laws are therefore not contradictory. They describe different scaling scenarios and use different reference frames.

However, Gustafson's Law still assumes that the serial fraction remains sufficiently stable and that communication and synchronization overhead do not grow excessively.

## 5. Conclusion

Measuring the serial fraction on the parallel machine resolves the apparent serial fraction invariance paradox by accounting for the actual execution conditions of a scaled workload.

Amdahl's Law is appropriate for fixed-size problems, while Gustafson's Law is appropriate for workloads that grow with the available processors.

The key distinction is the reference frame used to measure the serial fraction and the way problem size changes as processor count increases.
