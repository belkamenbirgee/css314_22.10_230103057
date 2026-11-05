# Task 05: Deconstructing the "Amdahl's Pessimism" Fallacy

## 1. Introduction

Amdahl's Law suggests that the serial portion of a program limits the maximum achievable speedup. However, Gustafson, Montry, and Benner demonstrated in 1988 that large speedups are possible when the problem size increases with the number of processors.

Their experiment used a 1,024-processor nCUBE 10 system and demonstrated speedups exceeding 1,000×, despite a serial fraction of approximately 0.4%.

## 2. Amdahl's Law Prediction

Amdahl's Law assumes a fixed problem size.

The formula is:

\[
S_A(P)=\frac{1}{s+\frac{1-s}{P}}
\]

Given:

\[
P=1024,\quad s=0.004
\]

Substituting:

\[
S_A(1024)=\frac{1}{0.004+\frac{0.996}{1024}}
\]

\[
S_A(1024)=\frac{1}{0.00497265625}
\]

Therefore:

\[
\boxed{S_A(1024)\approx201.10}
\]

Amdahl's Law predicts a speedup of approximately 201× under the fixed-size assumption.

## 3. Gustafson's Law Prediction

Gustafson's Law assumes that the workload increases with the number of processors.

The formula is:

\[
S_G(P)=P-\alpha(P-1)
\]

Given:

\[
P=1024,\quad \alpha=0.004
\]

Substituting:

\[
S_G(1024)=1024-0.004(1023)
\]

\[
S_G(1024)=1024-4.092
\]

Therefore:

\[
\boxed{S_G(1024)=1019.908}
\]

The scaled speedup is approximately 1,020×.

## 4. Why Problem Expansion Changes the Result

The main difference is the workload assumption.

Amdahl's Law distributes a fixed problem among more processors. The serial portion becomes a bottleneck as the parallel portion becomes faster.

Gustafson's Law increases the problem size as more processors become available. The parallel portion represents a larger total amount of work, while the parallel runtime remains approximately constant.

This allows the equivalent serial workload to grow substantially.

The experiment demonstrates that Amdahl's fixed-size speedup ceiling does not necessarily apply to scaled workloads.

## 5. Conclusion

The nCUBE 10 experiment illustrates the importance of weak scaling in parallel computing.

Amdahl's Law predicts approximately 201× speedup for a fixed workload, while Gustafson's Law predicts approximately 1,020× speedup under the scaled workload assumption.

The key lesson is that increasing problem size can make massive parallel speedup possible. Amdahl's Law is not incorrect; it describes a different scaling model.

