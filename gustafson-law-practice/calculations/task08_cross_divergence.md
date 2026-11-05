# Task 08: Amdahl vs. Gustafson — Cross-Model Divergence

## 1. Given Parameters

- Number of processors: \(P = 128\)
- Serial fraction: \(s = \alpha = 0.08\)
- Parallel fraction: \(1 - 0.08 = 0.92\)

## 2. Amdahl's Law Speedup

Amdahl's Law assumes a fixed problem size.

\[
S_A(P)=\frac{1}{s+\frac{1-s}{P}}
\]

Substitute the values:

\[
S_A(128)=\frac{1}{0.08+\frac{0.92}{128}}
\]

\[
S_A(128)=\frac{1}{0.08+0.0071875}
\]

\[
S_A(128)=\frac{1}{0.0871875}
\]

\[
\boxed{S_A(128)\approx11.47}
\]

## 3. Gustafson's Law Speedup

Gustafson's Law assumes that the problem size increases with the number of processors.

\[
S_G(P)=P-\alpha(P-1)
\]

Substitute the values:

\[
S_G(128)=128-0.08(128-1)
\]

\[
S_G(128)=128-0.08(127)
\]

\[
S_G(128)=128-10.16
\]

\[
\boxed{S_G(128)=117.84}
\]

## 4. Percentage Discrepancy

The difference between the two speedups is:

\[
\Delta S=S_G-S_A
\]

\[
\Delta S=117.84-11.47
\]

\[
\boxed{\Delta S\approx106.37}
\]

Using Amdahl's speedup as the reference:

\[
\text{Discrepancy}=
\frac{S_G-S_A}{S_A}\times100\%
\]

\[
=\frac{117.84-11.4695}{11.4695}\times100\%
\]

\[
\boxed{\text{Discrepancy}\approx927.42\%}
\]

Gustafson's predicted speedup is approximately 10.27 times Amdahl's prediction.

## 5. Explanation

The two models produce very different results because they use different assumptions.

Amdahl's Law assumes a fixed problem size. As the number of processors increases, the serial portion limits the maximum speedup.

Gustafson's Law assumes that the problem size grows with the number of processors. The serial portion remains relatively small while more work is performed in parallel.

Therefore, Gustafson's Law predicts a much higher speedup for large-scale parallel computing. The discrepancy becomes more significant as the number of processors increases.

## Conclusion

For 128 processors and a serial fraction of 0.08, Amdahl's Law predicts a speedup of approximately 11.47, while Gustafson's Law predicts 117.84. The relative discrepancy using Amdahl's result as the reference is approximately 927.42%. This demonstrates the importance of problem-size assumptions in evaluating parallel performance.