# Task 06: Parametric Speedup Across Processor Densities

## 1. Introduction

This task calculates theoretical scaled speedup and parallel efficiency for different processor counts using Gustafson's Law.

The given serial fraction is:

\[
\alpha=0.04
\]

The processor counts are:

\[
P=16,64,256,1024,4096,16384
\]

## 2. Mathematical Formulation

Gustafson's scaled speedup formula is:

\[
S(P)=P-\alpha(P-1)
\]

Substituting \(\alpha=0.04\):

\[
S(P)=P-0.04(P-1)
\]

Expanding:

\[
S(P)=P-0.04P+0.04
\]

Therefore:

\[
\boxed{S(P)=0.96P+0.04}
\]

Parallel efficiency is:

\[
E(P)=\frac{S(P)}{P}
\]

Substituting:

\[
E(P)=\frac{0.96P+0.04}{P}
\]

Therefore:

\[
\boxed{E(P)=0.96+\frac{0.04}{P}}
\]

## 3. Calculation Table

| P | S(P) | E(P) |
|---:|---:|---:|
| 16 | 15.40 | 96.2500% |
| 64 | 61.48 | 96.0625% |
| 256 | 245.80 | 96.0156% |
| 1,024 | 983.08 | 96.0039% |
| 4,096 | 3,932.20 | 96.0010% |
| 16,384 | 15,728.68 | 96.0002% |

## 4. Example Calculation

For \(P=16\):

\[
S(16)=16-0.04(16-1)
\]

\[
S(16)=16-0.6=15.4
\]

Efficiency:

\[
E(16)=\frac{15.4}{16}=0.9625
\]

\[
E(16)=96.25\%
\]

## 5. Analysis

As the number of processors increases, the scaled speedup increases almost linearly.

Parallel efficiency decreases slightly from 96.25% at 16 processors to approximately 96.0002% at 16,384 processors.

The efficiency approaches:

\[
\lim_{P\to\infty}E(P)=1-\alpha
\]

\[
\lim_{P\to\infty}E(P)=0.96
\]

Therefore, the theoretical asymptotic efficiency is 96%.

## 6. Conclusion

Gustafson's Law predicts high parallel efficiency for the given serial fraction of 4%. Increasing processor count significantly increases scaled speedup while efficiency remains close to 96%.

