# Mandelbrot Set - Parallel Task Decomposition Implementation and Analysis
This project was developed as part of the PAR (Parallelism) course at the FIB - UPC Barcelona. The focus is on the implementation and performance analysis of iterative and recursive task decomposition techniques using OpenMP for the computation of the Mandelbrot set. <br><br>

## Authors
- Arnau Claramunt
- David García

[![GitHub followers](https://img.shields.io/github/followers/ArnauCS03?label=ArnauCS03)](https://github.com/ArnauCS03) &nbsp;&nbsp; [![GitHub followers](https://img.shields.io/github/followers/dgarevalo?label=dgarevalo)](https://github.com/dgarevalo) <br><br>

## Iterative task decomposition

The **iterative task decomposition** approach involves dividing the Mandelbrot set computation into smaller tasks, which are then processed in parallel. The main goal is to exploit parallelism while handling dependencies and data sharing to avoid concurrency issues. To improve efficiency, strategies like finer grain tasks were employed. This involves breaking down the computation into even smaller, more manageable tasks that can be distributed across multiple threads.  <br><br>

Key Modifications:

- Implemented in *mandel-omp-iter-finer.c* *mandel-omp-iter-v1.c*
- Used `#pragma omp task` for task creation within nested loops.
- Applied **atomic** and **critical** operations to avoid data race conditions.  <br><br>

Performance Analysis:

- Model Factors Analysis: Evaluated the efficiency and overhead of the parallel implementation. Identified and addressed bottlenecks.
- Paraver Analysis: Used Paraver to visualize and analyze the execution traces for 16 threads.
- Strong Scalability: Conducted scalability tests to determine how the performance scales with an increasing number of threads.  <br><br>

## Recursive Task Decomposition

The **recursive task decomposition** approach uses a divide-and-conquer strategy to break down the computation into smaller sub-problems. Each sub-problem is solved recursively, leveraging parallel tasks where possible. This method utilizes leaf and tree strategies to optimize task execution and load balancing. In the leaf strategy, tasks are only created at the lowest level of recursion, reducing overhead. The tree strategy, on the other hand, creates tasks at multiple levels of recursion, improving load distribution but potentially increasing overhead.

Key Modifications:

- Implemented in *mandel-omp-rec-leaf.c* *mandel-omp-rec-tree.c*
- Addressed dependencies and data sharing to prevent concurrency issues.

Performance Analysis:

- Model Factors Analysis: Similar to the iterative approach, evaluated the efficiency and identified bottlenecks in the recursive implementation.
- Paraver Analysis: Analyzed execution traces with Paraver for 16 threads to understand task distribution and synchronization.
- Strong Scalability: Tested how well the implementation scales with an increasing number of threads. <br><br>

## Results and Comparison

The results show that both the iterative and recursive implementations achieve significant speedups compared to the sequential versions. However, the recursive task decomposition demonstrated better scalability and efficiency, making it the preferred approach for this problem.  <br><br>

### Summary of Execution Times:

Execution times were recorded for different thread counts (1, 4, 8, 12, 16, 20).
The recursive implementation consistently outperformed the iterative one in terms of scalability and overall execution time.  <br><br>

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

<br><br>

## Conclusion

This project successfully demonstrates the implementation and analysis of parallel task decomposition techniques for the Mandelbrot set computation. The recursive task decomposition, in particular, showed superior performance and scalability, making it a valuable approach for parallel computations in similar applications.
<br><br>

