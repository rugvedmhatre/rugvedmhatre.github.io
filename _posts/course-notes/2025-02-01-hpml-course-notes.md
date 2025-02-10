---
title: "Course Notes: High Performance Machine Learning"
date: 2025-02-01T18:31:00+05:30
toc: true
toc_label: "Notes"
category: course-notes
---

These are my notes on [High Performance Machine Learning]({{ site.url }}{{ site.baseurl }}/machine-learning/hpml-course/) course.

## Introduction to Benchmarking

### Coding Exercise

We learn and implement microbenchmarks to measure execution time, memory bandwidth, and compute FLOPS. This provides insights into system efficiency and computational throughput.

[Code](https://github.com/rugvedmhatre/HPC-Benchmarking)

### Quiz Yourself

1. With strong scaling, as we add more and more compute resources we can continue to get speedup since the amount of work per compute resource gets smaller and smaller.
    - [ ] True
    - [x] False

2. Cache blocking and SIMD are two techniques to improve software performance. Select all that is true about these techniques.
    - [x] If we enable SIMD we may increase the Arithmetic intensity.
    - [x] If we use cache blocking we may see an increase in FLOPS but the Arithmetic intensity remains unchanged.
    - [x] If we use cache blocking we may increase the Arithmetic intensity.
    - [x] If we enable SIMD we may see an increase in FLOPS but the Arithmetic intensity remains unchanged.

3. The list below shows the time (in sec) to complete 10000 floating point operations on an HPC compute node in 10 different runs.
    ```
    12, 13, 10, 12.5, 11, 11.25, 10.25, 14, 13.75, 14.25
    ```
    What is approximately the average throughput using the harmonic mean of throughputs obtained for individual runs?
    - [ ] 8.2 FLOPS
    - [ ] 82 FLOPS
    - [x] 820 FLOPS
    - [ ] 8200 FLOPS

4. Give the following code:
```C
for(k=1;k<N;k++){
    for(j=1;j<N;j++){
        for(i=1;i<N;i++){
            int ijk = i + j * jStride + k * kStride;
            new[ijk] = -6.0 * old[ijk] + old[ijk-1] + old[ijk+1] + old[ijk-jStride] +
                        old[ijk+jStride] + old[ijk-kStride] + old[ijk+kStride];
            new[ijk] = -8.15 * new[ijk]
        }
    }
}
```
    The code is executed on a system with DRAM bandwidth 51.2 GB/s and a 2-core processor with peak 81.3 GFLOPS per core. What is true about its Arithmetic Intensity (A.I.) and bottleneck with double precision floating point?
    - [ ] None of the options are correct
    - [x] A.I. is 0.125 FLOP/byte and its memory-bound
    - [ ] A.I. is 0.109 FLOP/byte and its compute-bound
    - [ ] A.I is 0.109 FLOP/byte and its memory-bound
    - [ ] A.I. is 0.125 FLOP/byte and its compute-bound

5. Consider a program using parallel processing and running on 5 CPUs in parallel. The total CPU time is 800 secs. What is the total elapsed time assuming the work is evenly distributed on each CPU and no wait is involved for I/O or other resources.
    - [ ] 805 secs
    - [x] 160 secs
    - [ ] 800 secs
    - [ ] 4000 secs

6. Which of the following graph represents Moore's law?
    <img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/hpml-course-notes/quiz1-q6.png" alt="Question 6 Image">
    - [x] Transistors
    - [ ] Thread Performance
    - [ ] Power
    - [ ] Logical Cores

7. Consider an Intel Xeon server with 8 cores and 3.5 GHz clock frequency and 32 DP FLOPs/cycle. Here DP stands for double precision (64 bit double). What is true about the peak FLOPS for this server.
    - [x] Its peak FLOPS is 896 GFLOPS for double precision arithmetic.
    - [x] Peak FLOPS can be jumped to about 1.8 TFLOPS (T for tera) by changing to single precision.
    - [x] Its peak FLOPS is 428 GLOPS for single precision arithmetic.
    - [x] When running at reduced clock frequency of 2.5 GHz, the peak FLOPS drop to 640 GLOPS

8. You need to create an application to process a database of customers for a bank and identify the top 1000 customers who can be targeted for marketing a new investment fund. 
    
    The application should query the database, process the query results, present the list of customers as an excel sheet with charts showing distribution of different statistics.
    
    You quickly wrote the application code and handed it to the performance testing team. The team identified that it takes around 15 minutes to run your code end-to-end. Further profiling revealed that 30% of the time is spent in running the database query, 50% in processing the query results, and the remaining 20% in creating the excel sheet. The product team says that the code will only be deployed if the runtime is brought down to 9 mins. Suppose you target to optimize the code to process the query results. How much speedup is needed in this part of the code so that you can meet the runtime target of 9 mins?
    - [ ] It cannot be determined from the information provided
    - [x] 5x
    - [ ] 4x
    - [ ] 1.67x
    - [ ] 0.8x

9. Which of the following is true for the Partition Model?
    - [x] Compute hardware with a different configuration than service & I/O
    - [x] Split the system physically into functional units
    - [x] Run all the softwares to perform a function
    - [x] It is only applicable to software

10. Show below is the output of a test program ran with time command on a linux machine.

    ```
    (base) root@ffl-robust-robust2:~# time ./a.out
    real    0m2.376s
    user    0m2.372s
    sys     0m0.004s
    ```
    What is the difference between CPU time and total elapsed time ?
    - [ ] 0.004 sec
    - [x] 0.000 sec
    - [ ] 2.372 sec
    - [ ] 2.368 sec

11. Which of the following is true? (\\(\subseteq \\) denotes subset. \\(A \subseteq B\\) implies \\(A\\) is subset of \\(B\\))
    - [ ] Machine Learning \\(\subseteq \\) Deep Learning \\(\subseteq \\) Artificial Intelligence
    - [ ] Artificial Intelligence \\(\subseteq \\) Machine Learning \\(\subseteq \\) Deep Learning
    - [ ] Artificial Intelligence \\(\subseteq \\) Deep Learning \\(\subseteq \\) Machine Learning
    - [x] Deep Learning \\(\subseteq \\) Machine Learning \\(\subseteq \\) Artificial Intelligence

12. What changes have we seen in the world of machine learning due to the advent of high performance computing?
    - [x] Moved to InfiBand like computer networking communications from standard networks
    - [x] Homogeneous to Heterogeneous computing
    - [x] Ability to handle and use terabytes of data

13. Which of the following is present in a Lightweight Kernel?
    - [x] Reduced Linux API
    - [x] File System Drivers
    - [x] TCP/IP Stack
    - [x] Process Management

14. Table below shows the speedups (as a ratio) obtained when running 10 different jobs on a V100 GPU over an Intel 2.53 GHz CPU.

    ```
    5, 3, 7.5, 2, 15, 1, 3, 5, 6, 2.5
    ```

    What is the best approximation for average speedup?
    - [ ] 15
    - [x] sqrt(15)
    - [ ] sqrt(5)
    - [ ] 5

15. What are the important features of high performance computing architecture?
    - [x] Power
    - [x] Efficiency
    - [x] Sequentiality
    - [x] Reliability
    - [x] Speed

16. You need to train a machine learning model. When the dataset is small you can easily train on one compute node in a reasonable amount of time. When the dataset is larger training on one node is very time consuming.

    Your friend suggests using multiple nodes for training with larger dataset by dividing the dataset equally among those nodes. When you did this, you were able to train using a larger dataset in roughly the same time as training using the smaller dataset on a single node. This is an example of \_\_\_ scaling.
    - [ ] strong
    - [x] weak
    - [ ] hybrid

17. Scalable System Software reduces operating system interrupts by stripping down OS running on compute nodes.
    - [x] True
    - [ ] False

18. Consider 5 different codes with measured performance marked by P1, P2, P3, P4, and P5 in the roofline performance model shown below:
    <img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/hpml-course-notes/quiz1-q18.png" alt="Question 18 Image">
    What can be inferred from this chart? Select all that apply.
    - [x] P1 and P2 are memory- bound and P3 is compute-bound.
    - [x] P1 and P2 are compute-bound but P3 and P4 are memory-bound
    - [x] P4 is not feasible with current CPU configuration in the system
    - [x] P5 is not feasible with current DRAM in the system

## Introduction to Profiling ML Models

### Coding Exercise

We implement a ResNet-18 model and train it on the CIFAR-10 dataset with various training configurations. We profile the performance, analyzing the impact of number of workers in data loaders, optimizers and batch norm layers.

[Code](https://github.com/rugvedmhatre/ResNet-Profiling)

## Introduction to Model Tuning

### Coding Exercise

We program a ChatBot trained using parameters obtained from a Weights & Biases (W&B) parameter sweep. We profile the model using PyTorch Profiler to analyze performance bottlenecks. Additionally, we create an optimized TorchScript version for efficient deployment.

[Code](https://github.com/rugvedmhatre/ChatBot-Tuning)

## Introduction to CUDA Programming

### Coding Exercise

We implement CUDA kernels for Matrix Multiplication, Unified Memory, and Convolution. We then benchmark GPU performance, measuring execution time, memory throughput, and computational efficiency.

[Code](https://github.com/rugvedmhatre/CUDA-Benchmarking)