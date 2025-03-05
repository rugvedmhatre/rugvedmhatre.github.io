---
title: "Course Notes: Data Science for Business"
date: 2025-03-05T18:30:00+05:30
toc: true
toc_label: "Notes"
category: course-notes
---

## What is Data Science?

The science of extracting knowledge and insights from data.

Examples of Data Science Projects:

- Network Analytics
- Social Networks and Marketting
- TV and Video Consumption
- Content Recommender Systems

## Data Science Process

We will be focussing on the CRISP Data Mining Process (CRISP-DM = Cross-Industry Standard Process for Data Mining)

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/dsb-course-notes/crisp-dm-image.png" 
alt="Figure 1: The CRISP Data Mining Process">
<figcaption><em>Figure 1: The CRISP Data Mining Process</em></figcaption>
</figure>

### Business Understanding

In this stage, the analysts' creativity plays a large role. The key to a great success is a creative problem formulation by some analyst regarding how to cast the business problem as one or more data science problems. High-level knowledge of the fundamentals helps creative business analysts see novel formulations.

One way to improve understanding is to try and break the big questions into smaller questions that are answerable by data.

__Big Questions__

- How do we increase revenue?
- How do we diversify customers?
- Why is customer satisfaction down?

__Small Questions__

- What are the properties of high-performing stores?
- Which population segments are buying less?
- What strategies reduce customer service hold times?

We will also improve our business understanding by asking the right questions to different stakeholders. This also means that we need to communicate our results to different groups in different ways.

__Stakeholders__

- Executive
- Sales
- Marketing
- Technology
- Operations

__Questions to ask__

- What is the goal of the solution?
- What data is available?
- What constraints exist?
- How do we evaluate?
- What does success look like?
- How will people act on the results?

### Data Understanding

It is important to understand the strengths and limitations of the data because rarely is there an exact match with the data science problem you're trying to solve.

One should know where the data comes from, we should connect with the teams that collected the data and understand how it was created. Secondly, we also need to know how to get the data from these teams, what systems or tools we require. Next, we understand the data by conductive exploratory data analysis (EDA). Finally, we also need know the limits of our data, and spend time cleaning, understanding it.

### Data Preparation

This stage involves transforming our data for modelling by conducting exploratory data analysis, missing data analysis, outlier detections and assesment, feature engineering and data munging.

One of the core concepts in data science and machine learning that separates it from statistics is the splitting of data into training and test sets.

We randomly partition the labelled dataset into training and test sets. 

- __Training set__ is a random selection of input data points (usually between 70%-90% of the original dataset size) which is used to build the model and estimate the model parameters. 
- We use the __test set__ (a.k.a. "hold-out set") which consists of the remaining data (10%-30% of the original dataset size) to asses the model's performance. We generate estimates of the "generalization error" - model's error on the test data.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/dsb-course-notes/training-test-split.png" 
alt="Figure 2: Training and Test Datasets">
<figcaption><em>Figure 2: Training and Test Datasets</em></figcaption>
</figure>

### Modelling

This is the stage where we apply machine learning algorithms to make predictions.

### Evaluation

The purpose of the evaluation stage is to assess the model results rigorously and to gain confidence that they are valid and reliable before moving on to deployment.

We must define numerical metrics to determine the best model or the appropriate model paramters to use. Some examples are RMSE (root mean square error), MAE (mean absolute error), ROC Curves (receiver operating characteristic curves).

The evaluation metric should be tied to the business problem. For example, in a recommender system, the popular items should score well. It is also important to understand how the metrics translate to practical significance, such as, what does RMSE mean for our particular use case. You may find that the "best" performance might not actually have practical significance.

Always ask: is the success metric of the evaluation aligned with the business need? We could compare our model's result to some baseline, or dumb models.

### Deployment

One critical aspect of every data science exercise in business is: what action will be taken?

Models don't have any business value until they get into production. Deployment decisions can effect the impact of the model. That is, deployments always has suprises. One way is to deploy slowly with pilot studies and A/B testing with careful monitoring and feedback loops.

Data science and the deployment teams (software engineers, DevOps, QA) should be integrated from the start to avoid any technical surprises.

__The CRISP-DM process should not stop here. It should iterate and continously improve!__

## Types of Data Science Tasks

### Supervised Learning

- There is a specific quantifiable target that we are interested in or trying to predict.
- Example, predict whether a customer will buy our product based on his/her browsing habits of our website.
- Algorithms like Decision Trees, Regression are used.

__Types of Supervised Learning Models__

- __Classification:__ The prediction variable is categorical (perhaps binary). Example, will the loan application default on their loan?
- __Regression:__ The prediction variable is numeric (continuous). Example, how much money will this customer spend on my product next year?
- __Time Series:__ Here the data is time based, and we are forecasting into the future. Example, what will my company stock close at next month?
- __Other Models:__ Predicting text or any other media. Example, what should my customer care chatbot say next?

### Unsupervised Learning

- There is no such quantifiable target, we are just trying to understand the data.
- Example, segment customer base into clusters that help define broad customer types.
- We use data visualizations, segmentation, clustering in this.

## Exploratory Data Analysis

<!-- To be continued... -->

## References

1. Provost, Foster, and Fawcett, Tom. Data Science for Business: What You Need to Know about Data Mining and Data-Analytic Thinking. United States, O'Reilly Media, 2013.
2. James, Gareth, et al. An Introduction to Statistical Learning: With Applications in Python. Germany, Springer International Publishing, 2023.
3. Shmueli, Galit, et al. Data Mining for Business Analytics: Concepts, Techniques, and Applications in R. Germany, Wiley, 2017.
4. Diez, David, et al. OpenIntro Statistics. United States, OpenIntro, Incorporated, 2019.
