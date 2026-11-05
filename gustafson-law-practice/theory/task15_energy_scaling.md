# Task 15: Energy Scaling in Parallel Computing

## 1. Introduction

Energy scaling describes how energy consumption changes when the number of processors increases.

Adding more processors can reduce execution time, but it can also increase total power consumption. Therefore, parallel performance should be evaluated using both speedup and energy efficiency.

## 2. Basic Energy Formula

Energy consumption is calculated as:

\[
E=P_{power}\times T
\]

where:
- \(E\) is energy consumption.
- \(P_{power}\) is average power.
- \(T\) is execution time.

For a parallel system:

\[
E_{parallel}=P_{parallel}\times T_{parallel}
\]

## 3. Relationship with Gustafson's Law

Gustafson's Law predicts speedup as:

\[
S(P)=P-\alpha(P-1)
\]

Execution time can decrease as more processors are used. However, total energy does not necessarily decrease because additional processors consume power.

If average power increases faster than execution time decreases, total energy consumption may increase.

## 4. Example Calculation

Assume a serial program takes 100 seconds and consumes 50 watts.

Serial energy:

\[
E_{serial}=50\times100=5000\ J
\]

Now assume a parallel version uses 8 processors, takes 20 seconds, and consumes 120 watts.

Parallel energy:

\[
E_{parallel}=120\times20=2400\ J
\]

Energy savings:

\[
5000-2400=2600\ J
\]

Percentage reduction:

\[
\frac{2600}{5000}\times100=52\%
\]

The parallel version uses 52% less energy in this example.

## 5. Energy Efficiency Considerations

Several factors influence energy scaling:

- Processor count: more processors can increase power consumption.
- Execution time: faster execution can reduce energy usage.
- Communication: transferring data between processors consumes energy.
- Hardware efficiency: newer processors may perform more operations per watt.
- Workload size: larger workloads may require more memory and computation.

## 6. Conclusion

Parallel computing can improve execution time and reduce energy consumption, but this is not guaranteed.

The best configuration should balance speedup, power consumption, and total energy. Therefore, energy efficiency should be measured alongside performance when evaluating parallel systems.