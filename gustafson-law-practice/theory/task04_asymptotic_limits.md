# Task 04: Asymptotic Analysis of Parallel Efficiency

## 1. Introduction

Parallel efficiency measures how effectively processors are utilized during parallel execution.

It is defined as:

\[
E(P)=\frac{S(P)}{P}
\]

This task analyzes the asymptotic behavior of efficiency under Gustafson's Law and compares it with Amdahl's Law as the number of processors approaches infinity.

## 2. Gustafson's Law Efficiency

Gustafson's scaled speedup is:

\[
S_G(P)=P-\alpha(P-1)
\]

Parallel efficiency is:

\[
E_G(P)=\frac{S_G(P)}{P}
\]

Substituting the speedup formula:

\[
E_G(P)=\frac{P-\alpha(P-1)}{P}
\]

Expanding the numerator:

\[
E_G(P)=\frac{P-\alpha P+\alpha}{P}
\]

Simplifying:

\[
E_G(P)=1-\alpha+\frac{\alpha}{P}
\]

Taking the limit as \(P\to\infty\):

\[
\lim_{P\to\infty}E_G(P)
=1-\alpha+\lim_{P\to\infty}\frac{\alpha}{P}
\]

Since:

\[
\lim_{P\to\infty}\frac{\alpha}{P}=0
\]

The final result is:

\[
\boxed{\lim_{P\to\infty}E_G(P)=1-\alpha}
\]

Therefore, Gustafson's Law predicts that efficiency approaches the parallel fraction of the workload.

## 3. Amdahl's Law Efficiency

Amdahl's speedup formula is:

\[
S_A(P)=\frac{1}{s+\frac{1-s}{P}}
\]

Efficiency is:

\[
E_A(P)=\frac{S_A(P)}{P}
\]

Substituting:

\[
E_A(P)=\frac{1}{P\left(s+\frac{1-s}{P}\right)}
\]

Simplifying:

\[
E_A(P)=\frac{1}{Ps+(1-s)}
\]

Taking the limit:

\[
\lim_{P\to\infty}E_A(P)
=\lim_{P\to\infty}\frac{1}{Ps+(1-s)}
\]

For \(s>0\), the denominator increases without bound.

Therefore:

\[
\boxed{\lim_{P\to\infty}E_A(P)=0}
\]

## 4. Comparison

| Model | Efficiency Formula | Limit as P → ∞ |
|---|---|---|
| Gustafson | \(1-\alpha+\frac{\alpha}{P}\) | \(1-\alpha\) |
| Amdahl | \(\frac{1}{Ps+(1-s)}\) | \(0\), if \(s>0\) |

Gustafson's Law maintains asymptotic efficiency because the workload grows with the number of processors. Amdahl's Law assumes a fixed problem size, so the serial portion increasingly limits processor utilization.

## 5. Conclusion

Under Gustafson's Law, parallel efficiency approaches \(1-\alpha\) as the processor count increases. Under Amdahl's Law, efficiency approaches zero for a nonzero serial fraction.

This demonstrates that weak scaling can maintain processor efficiency more effectively than strong scaling when the workload expands proportionally with available computing resources.
