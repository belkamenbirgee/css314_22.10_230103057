# Task 13: Failure Cases of Gustafson's Law

## 1. Introduction

Gustafson's Law explains how speedup can increase when the problem size grows with the number of processors. However, it assumes that the parallel workload can scale efficiently. In real systems, several factors can prevent this ideal scaling.

## 2. Main Failure Cases

### 1. Communication Overhead

Processors must exchange data during parallel execution. As the number of processors increases, communication can become expensive and reduce speedup.

**Example:** In a distributed application, processors frequently send data to each other. Network delays can make execution slower.

### 2. Load Imbalance

Not all processors may receive the same amount of work. Some processors finish early and wait for others.

**Example:** In image processing, some images may require more computation than others.

### 3. Memory Limitations

The system may not have enough memory to support a larger workload. Memory bandwidth can also become a bottleneck.

**Example:** Increasing the dataset size may cause frequent access to slower main memory.

### 4. Serial Operations

Some operations cannot be parallelized and must be executed sequentially. Their execution time limits the maximum speedup.

**Example:** A program may need to load data or initialize resources before parallel processing begins.

### 5. Synchronization Overhead

Parallel tasks sometimes need to wait for each other or access shared resources. Locks and synchronization can reduce performance.

**Example:** Multiple threads updating the same shared variable may need synchronization.

## 3. Comparison with the Ideal Model

| Factor | Effect on Performance |
|---|---|
| Communication | Adds data-transfer delays |
| Load imbalance | Causes processors to wait |
| Memory limitations | Restricts problem growth |
| Serial operations | Limits parallel execution |
| Synchronization | Adds waiting time |

Gustafson's Law assumes that the parallel portion grows efficiently. When these problems become significant, actual speedup becomes lower than the theoretical prediction.

## 4. Conclusion

Gustafson's Law is useful for understanding scalable parallel computing, but it does not describe every real-world limitation. Communication, load imbalance, memory limitations, serial operations, and synchronization can reduce performance.

Therefore, theoretical speedup should always be compared with real benchmark results.