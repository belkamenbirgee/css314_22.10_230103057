# Task 14: Isoefficiency Function

## 1. Introduction

Isoefficiency describes how fast a problem size must grow as the number of processors increases in order to maintain constant parallel efficiency.

It helps determine whether a parallel system can scale effectively.

## 2. Parallel Efficiency

Parallel efficiency is calculated as:

\[
E=\frac{S(P)}{P}
\]

where:
- \(E\) is parallel efficiency.
- \(S(P)\) is speedup.
- \(P\) is the number of processors.

Efficiency is also related to parallel overhead:

\[
E=\frac{W}{W+T_o}
\]

where:
- \(W\) is the useful computation time.
- \(T_o\) is the parallel overhead.

## 3. Isoefficiency Function

To maintain a constant efficiency, the problem size must grow enough to compensate for increasing overhead.

Starting with:

\[
E=\frac{W}{W+T_o}
\]

Rearranging:

\[
E(W+T_o)=W
\]

\[
ET_o=W(1-E)
\]

Therefore:

\[
\boxed{W=\frac{E}{1-E}T_o}
\]

For a fixed target efficiency, the problem size must grow proportionally to the parallel overhead.

This relationship is called the isoefficiency function.

## 4. Example

Assume the parallel overhead grows as:

\[
T_o(P)=P\log_2(P)
\]

To maintain an efficiency of 80%:

\[
E=0.8
\]

Using the isoefficiency equation:

\[
W=\frac{0.8}{1-0.8}P\log_2(P)
\]

\[
\boxed{W=4P\log_2(P)}
\]

For 16 processors:

\[
W=4(16)\log_2(16)
\]

\[
W=4(16)(4)=256
\]

For 64 processors:

\[
W=4(64)\log_2(64)
\]

\[
W=4(64)(6)=1536
\]

The problem size must increase from 256 to 1536 to maintain the same efficiency under this assumed overhead model.

## 5. Conclusion

The isoefficiency function shows how much the problem size must increase to maintain constant parallel efficiency.

A system with a low isoefficiency growth rate is generally easier to scale. A system with a high growth rate requires much larger problems as more processors are added.

Therefore, isoefficiency is an important measure for evaluating the scalability of parallel systems.