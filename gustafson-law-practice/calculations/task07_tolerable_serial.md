# Task 07: Reverse Engineering Maximum Tolerable Serial Overhead

## 1. Introduction

This task determines the maximum allowable serial fraction for a supercomputing cluster with 8,192 processing cores.

The required scaled speedup is at least 7,500.

Given:

\[
P=8192
\]

\[
S(P)\geq7500
\]

Gustafson's Law:

\[
S(P)=P-\alpha(P-1)
\]

## 2. Algebraic Derivation

Substitute the given values:

\[
8192-\alpha(8192-1)\geq7500
\]

Simplify:

\[
8192-8191\alpha\geq7500
\]

Subtract 8192 from both sides:

\[
-8191\alpha\geq-692
\]

Divide both sides by \(-8191\). The inequality direction reverses:

\[
\alpha\leq\frac{692}{8191}
\]

Therefore, the maximum allowable serial fraction is:

\[
\boxed{\alpha_{\max}=\frac{692}{8191}}
\]

## 3. Numerical Calculation

\[
\alpha_{\max}=\frac{692}{8191}
\]

\[
\alpha_{\max}\approx0.08448414
\]

Convert to percentage:

\[
\alpha_{\max}\times100
\]

\[
\boxed{\alpha_{\max}\approx8.4484\%}
\]

## 4. Verification

Substitute the maximum serial fraction into Gustafson's Law:

\[
S(8192)=8192-0.08448414(8191)
\]

\[
S(8192)\approx8192-692
\]

\[
\boxed{S(8192)\approx7500}
\]

The required speedup is satisfied.

## 5. Conclusion

The maximum allowable serial fraction is approximately 0.08448414, or 8.4484%.

To achieve a scaled speedup of at least 7,500 on 8,192 processors, the serial overhead must remain below or equal to this value.

