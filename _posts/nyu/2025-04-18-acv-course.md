---
title: "Advanced Topics in Computer Vision Course"
date: 2025-04-18T18:30:00+05:30
category: machine-learning
tags: nyu course
toc: true
seo_title: NYU Tandon - Advanced Topics in Computer Vision Course
excerpt: Overview of NYU Tandon's Advanced Topics in Computer Vision course (ECE-GY 9193) by David Fouhey
seo_description: Overview of NYU Tandon's Advanced Topics in Computer Vision course (ECE-GY 9193) by David Fouhey
---

*"Advanced Topics in Computer Vision" course (ECE-GY 9193) at NYU Tandon by [David Fouhey](https://cs.nyu.edu/~fouhey/)*

![nyu-header]({{ site.url }}{{ site.baseurl }}/assets/images/blog-images/nyu-tandon-logo.png)

"Advanced Topics in Computer Vision" course (ECE-GY 9193) at NYU Tandon, led by Professor [David Fouhey](https://cs.nyu.edu/~fouhey/), is a research-driven course that dives deep into cutting-edge developments in computer vision. Instead of traditional lectures, the course centers on reading, analyzing, and discussing recent academic papers. It’s designed for students who want to not only stay current with fast-moving advancements in vision research but also develop the skills needed to critically engage with research—reading thoughtfully, presenting clearly, and providing constructive feedback.

## Course Overview

This course explores the latest research in computer vision by engaging directly with recent papers from top conferences and journals. There is no textbook; instead, students read primary literature each week, learning to identify important contributions, evaluate the quality of experiments, and understand the broader implications of each work.

The course focuses on two key objectives: building a strong understanding of current vision research, and developing foundational research skills. Students practice reading papers critically, pitching ideas effectively, writing with clarity, presenting to both technical and non-technical audiences, and offering constructive peer feedback. These are not just skills for academic success, but essential tools for contributing meaningfully to the field.

Class sessions are structured around active participation. Each week, all students read the assigned paper(s) and an accompanying “big picture” reading that puts the work into broader context. A group of students prepares a presentation, while others take on the role of discussion leaders—tasked with asking thoughtful questions and guiding conversation. This format, inspired by the Role-Playing Paper Seminar by Alec Jacobson and Colin Raffel, breaks away from long, passive lectures and replaces them with collaborative, in-depth discussions.

A standout feature of the course is its emphasis on peer feedback. Students regularly give and receive feedback on presentations and participation. This process, moderated by the instructor and course assistants, encourages a supportive and intellectually honest environment. Feedback is not competitive—students are not ranked against each other—but is used to help everyone improve.

Overall, Advanced Topics in Computer Vision is ideal for students who want to explore state-of-the-art research, sharpen their academic communication skills, and gain a deeper understanding of how ideas in computer vision evolve and take shape. It’s not about memorizing algorithms—it’s about learning how to think, question, and contribute.

## Course Work and Grading

_Note: This is subject to change_

- Attendance - 20%
- Course Participation - 15%
- Presentations - 15%
- Project - 50%

## Readings

### Recognition and Basic Tasks (Data and Architectures)
- Technical Paper 1: Segment Anything, Alexander Kirillov et al. ICCV 2023
- Technical Paper 2: An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale, Alexey Dosovitsky et al. ICLR 2021
- Big Picture Paper: 50 Years of Data Science (Up to Page 18), David Donoho, 2015
- Reference Papers: 
  - Microsoft COCO: Common Objects in Context
  - End-to-End Object Detection with Transformers (DETR)
  - Deep Residual Learning for Image Recognition (ResNet)
  - Detecting Twenty-thousand Classes using Image-level Supervision

### Vision and Language Models
- Technical Paper 1: Flamingo: a Visual Language Model for Few-Shot Learning, Jean-Baptiste Alayrac et al., NeurIPS 2022
- Technical Paper 2: Visual Instruction Tuning, Haotian Liu et al. NeurIPS 2023
- Big Picture Paper: Scaling Laws for Neural Language Models, Jared Kaplan et al., 2020
- Reference Papers: 
  - Learning Transferable Visual Models From Natural Language Supervision
  - VQA: Visual Question Answering
  - Language Models are Few-Shot Learners

### Diffusion
- Technical Paper 1: Denoising Diffusion Probabilistic Models, Jonathan Ho, Neurips 2020
- Technical Paper 2: Scalable Diffusion Models with Transformers, William Peebles and Saining Xie, ICCV 2023
- Big Picture Paper: Heilmeir Catechism, George Heilmeir, 1970s
- Reference Papers: 
  - Deep Unsupervised Learning using Nonequilibrium Thermodynamics (harder read – it’s math-heavy)
  - Conditional Image Generation with PixelCNN Decoders
  - Texture Synthesis By Non-Parametric Sampling
  - Neural Discrete Representation Learning
  - High-Resolution Image Synthesis with Latent Diffusion Models

### Datasets
- Technical Paper 1: PASS: An ImageNet replacement for self-supervised pretraining without humans, Yuki Asano et al. 
- Technical Paper 2: Do ImageNet Classifiers Generalize to ImageNet?, Benjamin Recht et al. ICML 2019
- Big Picture Paper: Are We Learning Yet?, Thomas Liao et al., 2021
- Reference Papers: 
  - ImageNet: A Large-Scale Hierarchical Image Database
  - Unbiased Look at Dataset Bias
  - Does Object Recognition Work for Everyone? 

### Multiview 3D
- Technical Paper 1: DUSt3R: Geometric 3D Vision Made Easy, Shuzhe Wang et al. CVPR 2024
- Technical Paper 2: VGGSfM: Visual Geometry Grounded Deep Structure From Motion, Jianyuan Wang et al. CVPR 2024
- Big Picture Paper: Unreasonable effectiveness of data, Alon Halevy, Peter Norvig, and Fernando Pereira, 2009
- Reference Papers:
  - Structure-from-Motion Revisited
  - Building Rome in a Day 
  - SuperGlue: Learning Feature Matching with Graph Neural Networks

### Neural Fields
- Technical Paper 1: 3D Gaussian Splatting for Real-Time Radiance Field Rendering, Bernhard Kerbl. SIGGRAPH 2023
- Technical Paper 2: Mip-NeRF, Jonathan Barron et al. ICCV 2021
- Big Picture Paper: What Makes a (Graphics) Systems Paper Beautiful, Kayvon Fatahlian, ??
- Reference Papers: 
  - NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis
  - Fourier Features Let Networks Learn High Frequency Functions in Low Dimensional Domains
  - Plenoxels: Radiance Fields without Neural Networks

### Single-View 3D
- Technical Paper 1: UniDepth: Universal Monocular Metric Depth Estimation, Luigi Piccinelli et al. CVPR 2024
- Technical Paper 2: CAT3D: Create Anything in 3D with Multi-View Diffusion Models, Ruiqi Gao and Aleksander Holynski et al., Arxiv 2024.
- Big Picture Paper: Statistical Learning: The Two Cultures, Leo Breiman, 2001
- Reference Papers: 
  - NYU v2 Dataset
  - Learning a predictable and generative vector representation for objects
  - Learning to Recover 3D Scene Shape from a Single Image

### Self-Supervised Learning
- Technical Paper 1: 4M-21: An Any-to-Any Vision Model for Tens of Tasks and Modalities, Roman Bachmann et al. Arxiv 2024
- Technical Paper 2: ImageBind: One Embedding Space To Bind Them All, Rohit Girdhar et al., CVPR 2023
- Big Picture Paper: Data Science at the Singularity, David Donoho, 2023
- Reference Papers: 
  - Unsupervised Visual Representation Learning by Context Prediction
  - Masked Autoencoders Are Scalable Vision Learners
  - A Cookbook of Self-Supervised Learning

### Egocentric Vision
- Technical Paper 1: Rescaling Egocentric Vision, Dima Damen et al. IJCV 2021
- Technical Paper 2: Ego-Exo4D, Kristen Grauman et al. Arxiv 2024
- Big Picture Paper: The Development of Embodied Cognition: Six Lessons from Babies, Linda Smith and Michael Gasser, 2005
- Reference Papers: 
  - Understanding Egocentric Activities 

### Humans
- Technical Paper 1: 3D Hand Pose Estimation in Everyday Egocentric Images, Aditya Prakash et al., ECCV 2024
- Technical Paper 2: Humans in 4D: Reconstructing and Tracking Humans with Transformers, Shubham Goel et al. ICCV 2023
- Big Picture Paper: SORA, SORA Team, 2024
- Reference Papers: 
  - SMPL: A Skinned Multi-Person Linear Model
  - Embodied Hands: Modeling and Capturing Hands and Bodies Together
  - End-to-end Recovery of Human Shape and Pose
  - Learning joint reconstruction of hands and manipulated objects

### Robotics
- Technical Paper 1: Open x-embodiment: Robotic learning datasets and rt-x models, The Open-X Embodiment Collaboration, Arxiv 2023.
- Technical Paper 2: On bringing robots home, Nur Muhammad Mahi Shafiullah, Arxiv 2023
- Big Picture Paper: Intelligence without representation, Rodney Brooks, 1987
- Reference Papers: 
  - Supersizing Self-supervision: Learning to Grasp from 50K Tries and 700 Robot Hours
  - Real-World Robot Learning with Masked Visual Pre-training
  - RMA: Rapid Motor Adaptation for Legged Robots

### Science
- Technical Paper 1: AstroCLIP: a cross-modal foundation model for galaxies, Liam Parker et al., Monthly Notices of the Royal Astronomical Society, 2024
- Technical Paper 2: Gravitationally Lensed Black Hole Emission Tomography, Aviad Levis et al. CVPR 2022
- Big Picture Paper: Position: Is machine learning good or bad for the natural sciences?, David Hogg and Soledad Villar, 2024

## Review

Professor David Fouhey is an excellent instructor who brings energy, clarity, and curiosity into every session. He has a talent for breaking down complex research papers into clear, understandable insights, and asks thoughtful questions that push students to think more critically.

This course stands out for its unique format. It doesn’t cover computer vision fundamentals or teach machine learning/deep learning basics—instead, it assumes you’re already familiar with them. The focus is on exploring cutting-edge research, which makes it especially exciting for students and aspiring researchers looking to dive deeper into real-world applications of deep learning in computer vision.

If you’re passionate about staying at the forefront of vision research and want to improve your ability to analyze, present, and discuss academic work, this course is a must-take.