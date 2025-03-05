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

Understanding your data goes hand and hand with the business problem you're trying to solve.

__Finding Data__

- In business critical systems, the main challenge is data cleaning. The systems are often set up for collection of data, as they are for running a business.
- We can find data online, but companies do not share critical data, and if they do, it is via a rate limited API. To collect online data, we can use parsers, scrapers, and other tools. BeautifulSoup is a python module that can be used to scrape websites. We could also use GenAI to get data.
- We cane rely on curated data science websites like UCI repository. The challenge in this case is that the dataset is sanitized and already much analyzed.

__Reading Data in Python__

Ideally the data that we will access will come to us in a nice Excel or CSV. However, this is not true in real life, we need to deal with database accesses, SQL or streaming data.

Reading the data in CSV requires the `pandas` module and the `pd.read_csv()` function, with the file name or the URL of the data.

__Exploring Data through EDA__

- Study and understand each feature
- Know the feature types and distributions
- Identify outliers
- Consider data transformations
- Identify missing data
- Visualize the data

### Feature Types

- __Numeric:__ Features where calculations are meaningful
- __Categorical:__ Features where we cannot do meaningful calculations. They can be multivalued, or might have numeric labels. Also check how the categories are ordered:
    - Ordinal: Income (A: 0-50k, B: 50k-100k, C: 100k-500k, D: >500k)
    - Nominal: Eye color (A: Blue, B: Brown, C: Green, D: Other)
- __Binary:__ Only two possible values - 0 and 1. (it is a special case of categorical feature type)
- __Date Stamps:__ Always check the date format. They can be considered as a numeric if not treated carefully. (Python uses `datetime` library)

Things can get messy very easily. For example, data about names, SSNs, credit ratings, zip codes, text, images or sound. You need to make sure that the software recognizes the right data type.

__Manipulating data in Python__

- Renaming variables (`.rename`)
- Summaries of variables (`.info` and `.describe`)
- Exploring data (`.head` and `.tail`)
- Viewing slices of data (`.loc` and `.iloc`)
- Categorical variables (`.value_counts`)
- Merging and splitting attributes (`.concat`, `.split`)
- Also can use sampling if the data is too large (`.sample`)

__Encoding Categorical Variables__

For example, we have categorical data for diet types: vegan, vegetarian, pescatarian and omnivore. We can recode this variable as *k* binary (0, 1) indicator variables (also called as dummy variables or one-hot encoding). Note that: we only need *k - 1* dummies to encode the information.

For some methods (like regression) you must encode with *k - 1* dummies to avoid an error.

| Category | isVegan | isVegetarian | isPescatarian |
| --- | --- | --- | --- |
| Vegan | 1 | 0 | 0 |
| Vegetarian | 0 | 1 | 0 |
| Pescatarian | 0 | 0 | 1 |

If all values are 0, then it belongs to Omnivore category.

You can use the `pd.get_dummies(drop_first=True)` or `sklearn.preprocessing.OneHotEncoder(drop='first')` in Python.

Another issue with dealing with categorical variables is that there can be too many levels, which can make the model complicated and messy. We may then want to transform the data only to the top levels and an 'others' category.

### Outliers

Outliers are observations that are far from the mean, and fall outside the range of most of the data.

We can find outliers using summary tables, data visualization or simple data sorting.

Outliers typically are attributable to one of the following causes: 

- The measurement is observed, recorded or entered incorrectly (e.g. blood pressure = -50)
- The measurement comes from a different set of population (e.g. age = 5 in a data about adults)
- The measurement is correct, but represents a rare (chance) event (e.g. people with net worth of billions of dollars in a dataset about general population)

Outliers should always be considered and inspected to see if they are "real" or some artifact of data collection.

__To Remove or Not To Remove__

- Outliers can have an outsize impact on analysis. You may choose to remove an outlier, even if it legitimate, just to avoid influence on the analysis.
- You can choose a robust analysis technique like Decision Trees. Regression is sensitive to outliers.
- Carefully assess data for legitimacy. If appears incorrect, remove it.
- Do not blindly use the automated outlier-finding algorithms (like IQR rule)

### Skewed Data

Highly skewed data can be problematic in data science analysis, especially with regression models (linear and logistic). Such skewed data can obscure pattern and invalidate statistically tests. One way to resolve skewed datasets is by using log-scale, square roots, or binning.

### Missing Data

Data points that are not recorded or are absent in the dataset are missing datapoints. They can be represented as '.', 'NA', '-1', etc. (Python uses `NaN` for missing values)

Reasons for missing data:
- data entry errors
- non-responses in surveys
- system errors, etc.

Missing data considerations:
- How much is there?
- Is it missing at random?
- Is missing-ness important by itself?
- How does the model handle it?

Pandas functions - `isnull()` and `notnull()` are used to detect missing values.

__Strategies for Missing Data__

- Deletion Methods:
    - Row deletion: remove the entire row if any value is NA
    - Column deletion: delete features with high percentage of NA. (impact of analysis needs to evaluated, as it could be drastic)
- Imputation Methods:
    - Mean/Median/Mode Imputation: replace all the NAs with mean, median or mode of the feature
    - Modeled Imputation: use algorithms like regression or k-nearest neighbours to predict and fill missing values
- Interpolation: Give data points the average of the two observations surrounding it (relevant for time series)
- Create a new category for NA

It is important to evaluate how much influence does your strategy have on the final conclusions.

Pandas functions - `dropna()` is used to drop rows or columns with missing values, `fillna()` is used to fill missing values with a specific value or method (mean, median or mode).

ScikitLearn functions - `SimpleImputer()` applies basic imputation strategies and `IterativeImputer()` applies modelling based imputation.

### Data Visualization


 

## References

1. Provost, Foster, and Fawcett, Tom. Data Science for Business: What You Need to Know about Data Mining and Data-Analytic Thinking. United States, O'Reilly Media, 2013.
2. James, Gareth, et al. An Introduction to Statistical Learning: With Applications in Python. Germany, Springer International Publishing, 2023.
3. Shmueli, Galit, et al. Data Mining for Business Analytics: Concepts, Techniques, and Applications in R. Germany, Wiley, 2017.
4. Diez, David, et al. OpenIntro Statistics. United States, OpenIntro, Incorporated, 2019.
