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