# Mandelbrot Set - Parallel Task Decomposition Implementation and Analysis
This project was developed as part of the PAR (Parallelism) course at the FIB - UPC Barcelona. The focus is on the implementation and performance analysis of iterative and recursive task decomposition techniques using OpenMP for the computation of the Mandelbrot set. <br><br>

## Authors


## Iterative task decomposition

The **iterative task decomposition** approach involves dividing the Mandelbrot set computation into smaller tasks, which are then processed in parallel. The main goal is to exploit parallelism while handling dependencies and data sharing to avoid concurrency issues.

Key Modifications:

- Implemented in *mandel-omp-iter.c*
- Used `#pragma omp task` for task creation within nested loops.
- Applied atomic operations to update shared resources safely.

Performance Analysis:

- Model Factors Analysis: Evaluated the efficiency and overhead of the parallel implementation. Identified and addressed bottlenecks.
- Paraver Analysis: Used Paraver to visualize and analyze the execution traces for 16 threads.
- Strong Scalability: Conducted scalability tests to determine how the performance scales with an increasing number of threads.

## Recursive Task Decomposition

The **recursive task decomposition** approach uses a divide-and-conquer strategy to break down the computation into smaller sub-problems. Each sub-problem is solved recursively, leveraging parallel tasks where possible.

Key Modifications:

- Implemented in mandel-omp-rec.c
- Used #pragma omp task for parallel task creation within the recursive calls.
- Addressed dependencies and data sharing to prevent concurrency issues.

Performance Analysis:

- Model Factors Analysis: Similar to the iterative approach, evaluated the efficiency and identified bottlenecks in the recursive implementation.
- Paraver Analysis: Analyzed execution traces with Paraver for 16 threads to understand task distribution and synchronization.
- Strong Scalability: Tested how well the implementation scales with an increasing number of threads.

## Experimental Setup

The experimental setup includes both the iterative and recursive implementations, along with the necessary scripts for compilation and execution. The provided files include:

- *mandel-seq-iter.c* and *mandel-seq-rec.c*: Sequential implementations.
- *mandel-omp-iter.c* and *mandel-omp-rec.c*: Parallel implementations.
- Various submit scripts for running and analyzing the performance of the implementations.

## Results and Comparison

The results show that both the iterative and recursive implementations achieve significant speedups compared to the sequential versions. However, the recursive task decomposition demonstrated better scalability and efficiency, making it the preferred approach for this problem.

Summary of Execution Times:

Execution times were recorded for different thread counts (1, 4, 8, 12, 16, 20).
The recursive implementation consistently outperformed the iterative one in terms of scalability and overall execution time.

## How to Run the Code

Compile the Code:
```
make
```

### Run the Parallel Code: (We used the Boada Supercomputer)
```
sbatch submit-omp.sh mandel-omp-iter 20
sbatch submit-omp.sh mandel-omp-rec 20
```

## Conclusion

This project successfully demonstrates the implementation and analysis of parallel task decomposition techniques for the Mandelbrot set computation. The recursive task decomposition, in particular, showed superior performance and scalability, making it a valuable approach for parallel computations in similar applications.
