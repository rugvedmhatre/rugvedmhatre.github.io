---
title: "Projects"
permalink: /projects/
---

![alt]({{ site.url }}{{ site.baseurl }}/assets/images/projects-header.png)
{: .full}

# Predictive Analysis of Diabetes

This project, conducted as part of the NYU Data Science bootcamp, focuses on predictive analysis within the PIMA Indian population, specifically aiming to predict the occurrence of diabetes. 

Leveraging machine learning techniques, the study delves into the analysis of a comprehensive dataset, investigating correlations and patterns to enhance predictive accuracy. 

Employing a K-Nearest Neighbors (KNN) model as a foundational approach, the project explores avenues for improved modeling and feature engineering to better predict diabetes occurrences within this demographic. 

Ultimately, the goal is to contribute to healthcare solutions and strategies tailored to address diabetes prevalence among the PIMA community.

[Checkout the code here...](https://github.com/rugvedmhatre/NYU-Data-Science-Bootcamp/blob/main/Project/Project-Analysis.ipynb)

# Autonomous Vehicle Simulation

Using CARLA simulator, captured a dataset using the camera and ran a semantic segmentation model.

Using U-Nets, I was able to segment the images with **96%** accuracy.

Further, I used the drivable surface segment from the output as a region of interest for the Lane Detection Algorithm.

Using Canny Edge Detection and Hough Line Transform, was able to extract the lanes from the image.

Finally, trained a traffic sign image classifier model to identify traffic signs in the environment.

[Checkout the code here...](https://github.com/rugvedmhatre/autonomous-vehicle/blob/main/image-semantic-segmentation.ipynb)

# Handwritten Digit Recognizer

Using Python NumPy arrays, I developed a neural network and implemented the activation functions, forward propagation procedures and back propagation procedures.

Downloaded the MNIST dataset from [Kaggle](https://www.kaggle.com/competitions/digit-recognizer/data) and trained a model with an accuracy of **87%**.

[Checkout the code here...](https://github.com/rugvedmhatre/handwritten-digit-recognizer/blob/main/Handwritten%20Digit%20Recognizer%20using%20Neural%20Network.ipynb)

# Pong Game

I was always interested to play old arcade 8-bit games. When I learned Assembly Programming, I decided to develop an old arcade game in it.

I researched for interrupts to display pixels on the screen, read system clock and read keyboard inputs. 

Implementing all these complex procedures, I created a Pong Game with three user screens:
1. Main Menu - Here the user can select which mode one wants to play. There are three options - single player mode, multiplayer mode and exit game option.
2. Game Screen - Depending on the user's choice, the game will start in single player mode or a two player mode.
3. Game Over Screen - The player that reaches 5 points first wins the game. On this screen the result is declared and the user is given a choice to restart the game or quit to main menu.

[Checkout the code here...](https://github.com/rugvedmhatre/pong/blob/main/PONG.ASM)

# Other Projects

- [Support Vector Machine Classifier](https://github.com/rugvedmhatre/SVM-Classifier)
- [Single Cycle MIPS Simulator in C++](https://github.com/rugvedmhatre/MIPS-Simulator)
- [MIPS 5-Stage Pipeline Simulator in C++](https://github.com/rugvedmhatre/MIPS-Pipeline-Simulator)
- [Two-Level Cache Simulator in C++](https://github.com/rugvedmhatre/Cache-Simulator)
- [Virtual Memory Simulator in C++](https://github.com/rugvedmhatre/Virtual-Memory-Simulator)
- [Branch Predictor Simulator in C++](https://github.com/rugvedmhatre/Branch-Predictor)
- [Tomasulo's Algorithm Simulator in C++](https://github.com/rugvedmhatre/Tomasulos-Algorithm)