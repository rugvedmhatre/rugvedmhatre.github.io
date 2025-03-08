---
title: "Course Notes: Data Science for Business"
date: 2025-03-06T18:30:00+05:30
toc: true
toc_label: "Notes"
category: course-notes
excerpt: Course notes on Data Science for Business course offered by New York University (NYU) Stern School of Business.
seo_title: NYU Stern Data Science for Business Course Notes
seo_description: Course notes on Data Science for Business course offered by New York University (NYU) Stern School of Business.
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

Looking carefully at the data is an important part of the exploratory process:

- to identify mistakes in collection/processing
- to find violations of statistical assumptions
- to observe patterns in the data

Sometimes a good, simple visualization is all the "analysis" you need.

However, data visualization is a challenging topic - very hard to do well - many design decisions to make. There are in-depth courses, that discuss the theories which cover things like - what do humans perceive well, how to use marks, colors, etc. Careful thought should be taken with the message you're trying to convey with your data.

It is always best to start to simple with the basic building blocks of visualizations - histograms, boxplots, scatterplots.

__Histograms__

Histograms are probably the most used (and useful) way to present numerical data. They provide a quick view of the range, distribution shape, outliers and trends in the data.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/dsb-course-notes/histogram_example.png" 
alt="Figure 3: Data Visualization - Histogram">
<figcaption><em>Figure 3: Data Visualization - Histogram</em></figcaption>
</figure>

The number of bins and bin-widths can have a role in the interpretation.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/dsb-course-notes/histogram_example_2.png" 
alt="Figure 4: Histogram with more bins">
<figcaption><em>Figure 4: Histogram with more bins</em></figcaption>
</figure>

__Boxplots__

A boxplot is another way of getting a quick visual clue of the key points of the data distribution. 

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/dsb-course-notes/boxplot.png" 
alt="Figure 5: Data Visualization - Boxplot">
<figcaption><em>Figure 5: Data Visualization - Boxplot</em></figcaption>
</figure>

__Multiple Variables__

You can represent contingency tables using [stacked bars](https://matplotlib.org/stable/gallery/lines_bars_and_markers/bar_stacked.html), [side-by-side bars](https://matplotlib.org/stable/gallery/lines_bars_and_markers/barchart.html) or [standardized bars](https://www.geeksforgeeks.org/stacked-percentage-bar-plot-in-matplotlib/).

Also, side by side boxplots allows you to compare numeric distributions across variables which are categorical.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/dsb-course-notes/multiple_boxplot.png" 
alt="Figure 6: Data Visualization - Multiple Boxplots">
<figcaption><em>Figure 6: Data Visualization - Multiple Boxplots</em></figcaption>
</figure>

For multiple numeric variables, scatter plot is the standard tool. It can be used to display the relation between two variables. We can easily see if there is any correlation between the data points plotted on the x-axis and the y-axis, or we can even find any strange patterns in the data, identify outliers, etc.
When you are dealing with overplotting, you can use "alpha blending" (i.e. transparency) or heatmaps.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/dsb-course-notes/scatterplot.png" 
alt="Figure 7: Data Visualization - Scatterplot">
<figcaption><em>Figure 7: Data Visualization - Scatterplot</em></figcaption>
</figure>

__From Exploration to Model Fitting__

Fitting data science models, follows the same basic structure:

- Instantiate a model
    ```python
    from sklearn.linear_model import LinearRegression

    model = LinearRegression()
    ```
- Identify X (predictors) and Y (target) and then create training and test sets.
    ```python
    from sklearn.model_selection import train_test_split

    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
    ```
- Use `.fit` to apply the model to the data
    ```python
    model.fit(X_train, y_train)
    ```
- Explore the outcomes of the model
    ```python
    y_pred = model.predict(X_test)
    ```
- Calculate model fit metrics
    ```python
    from sklearn.metrics import root_mean_squared_error    

    rmse = root_mean_squared_error(y_test, y_pred)
    ```

We do this over and over again.

## Decision Trees

Decision trees are one of the most useful and interpretable ways to build a predictive, supervised machine learning model.

There are very easy to interpret.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/dsb-course-notes/engineering-flowchart.jpeg" 
alt="Figure 8: Decision Tree Example">
<figcaption><em>Figure 8: Decision Tree Example</em></figcaption>
</figure>

- We start of with all the data. 
- At each level, we create a rule that creates "branches" (typically 2). 
- Each branch then can split independently. 
- Each level is defined by a rule. 
- Bottom level are called the "leaves". 
- Each data point falls in one and only one leaf
- Each leaf is defined by a set of rules that got us there
- Each leaf gets labelled with the majority class for those that fell in the leaf.
- Thus, new data can now be classified - every new instance goes to a single leaf.

__Nodes__

Numeric attributes are split at an "optimal" spot at the nodes

__Leaves__

Prediction for a new case is the majority class in the leaf node.

__Class Probabilities__

We can also assign a class probability to a new data point from the leaf node it falls into. Trees assign probabilities by looking at the proportion of the training labels that fell into each leaf node.

__Probability Correction__

\\[
\text{Laplace Correction} = p(c) = \frac{n + 1}{N + 2}
\\]

Where \\(n\\) is the number of examples in the leaf belonging to the class, and \\(N\\) is the total number of cases.

Laplace correction is often used in cases with small datasets, to offset the impact of "overfitting". 

__Overfitting__

The larger you build the tree, the more accurate it gets... on the training set. 😕

Applying a tree against a test set allows us to determine the optimal size of the tree to maximize for generalization, and avoid overfitting.

### Why Decision Trees?

Trees are one of the most popular models for supervised classification. Trees are easy to understand (when small), easy to communicate to executives and non-technical stakeholders, and they work pretty well for a simple model.

Trees are also computationally cheap for large datasets, can handle large sets of attributes easily, ignores irrelevant variables, handles missing data well, and doesn't make any distributional assumptions (compared to regression).

### Growing a Tree

There are two elements to a good split:
- "purity" of the branches
- "coverage" of the data

__Measuring Impurity__

The more homogeneous (consistent) a group is, the more pure it is. We measure purity with entropy:

\\[
\text{Entropy} = - p\_1 \log\_2(p\_1) - p\_2 \log\_2(p\_2)
\\]

Entropy is maximized when the classes are equally distributed, and the least when only one class exists in the sample at a time.
_(Note: Entropy also extends to more than two classes)_

\\[
\text{Low Entropy} = \text{More Information}
\\]

__How do we use Entropy?__
- A decrease in entropy means more information
- We calculate entropy before and after the split
- We evaluate the potential split by taking the overall entropy of the split (a weighted average of the two entropies).

__Measuring Coverage__

Entropy gives us a measure of how helpful a given leaf is in predicting the target. But we need an overall sense of the value of the split. We want splits that increase our overall information, not just carve off little areas with perfect entropy. We do this by measuring the overall improvement in entropy across the entire dataset for each split. 

\\[
\text{Information Gain} = \text{Impurity (parent)} - \text{Impurity (children)}
\\]

__Finding the Best Split__

At each split we need to:
- Find the optimal split point for each numeric attribute
- Find the optimal split for any categorical attribute
- Compare the information gain of those splits for each attribute
- Pick the best one and split

However, if we follow these rules, we can keep splitting and growing the tree until we have perfect purity or we find no splits that can add information.

But we don't want to grow as far as we can. Fewer nodes are typically better, more comprehensible and more accurate. Test (hold-out) sets will guide us in finding the optimal tree size.

Tree can also be interpreted geometrically - trees create rules that correspond to axis-parallel lines.

__Information Gain for Insight__

Each split of the decision tree results in information gain - decreasing entropy is information gain. We can assign the information gain to the attribute used for the split. Thus, information gain can give us a measure of **feature importance**.

__Random Forests__

Typically multiple trees (or forests) will outperform a single well-built tree. 

Random Forests is a machine learning method that fits many different trees to a prediction problem - using random samples of rows and columns - and averaging the prediction across trees. This results in an improved predictive power, however, at the loss of interpretability.

```python
from sklearn.ensemble import RandomForestClassifier
```

## Evaluating Models

If we apply accuracy to trees built on the training set, the biggest tree will always be best. In fact, you can often build a tree with 100% accuracy on the training set. But the goal is to generalize to data we have not seen yet.

We split the data into training and test sets, so that it provides a better estimate of model performance in the "real world" and optimize the value of model parameters (e.g. tree\_depth)

We typically have to scale back on model complexity in order to improve generalization error.

__Complexity vs. Error__

This is one of the most important concepts of machine learning:
- Models always get better (as measured on training set) with more data or more complexity
- But need holdout data to optimize generalizability

Overfitting: model is too complex: the model fits great on the training data but doesn't generalize to holdout data becuase it is "memorizing" the training data.

Complexity parameters:
- Tree Models: number of nodes, min. leaf size
- Regression Models: number of features, degree of polynomial, interactions
- Neural Networks: number of layers, complexity of functions

### Cross Validation

To get a better generalization error estimate, we need to account for the randomness of the split, by doing multiple splits. Cross-validation is one way to get around this.

Cross Validation Algorithm:
- Split data into \\(k\\) equal sets, called *folds*
- Fit model with sets \\((1, \dots, k - 1)\\), measure performance on fold \\(k\\). Subsequently fit \\(k\\) times using each fold as a hold-out.
- For each iteration, measure predictive performance, or the metric of interest

```python
from sklearn.model_selection import cross_val_score

cross_val_score(model, X, y, scoring='accuracy', cv=5)
```

### Leave One Out Cross Validation (LOOCV)

- Fit model on all but one data point
- Predict on the single data point and measure error
- Do that N times, once for each data point

LOOCV is the best in terms of estimating true error. But it can be very time-consuming, not necessary or larger data sets.

```python
from sklearn.model_selection import LeaveOneOut, cross_val_score

loo = LeaveOneOut()
cross_val_score(model, X, y, scoring='accuracy', cv=loo)
```

### Validation Set

- The test set serves two purposes: to find the best parameters and to estimate the out-of-sample error - so it is not really an "unbiased" estimate of error.
- In some cases, it may be useful to create a third parition of the data.
- This provides a truly untouched data set that gives the most accurate estimate of error
- Process:
    - Put aside a random 10%-20%
    - Split remaining data as normal into training and validation sets
    - Use training/validation to set parameters (e.g. optimal tree\_depth) and then simply apply to the holdout data

## Evaluating Classification Models



## References

1. Provost, Foster, and Fawcett, Tom. Data Science for Business: What You Need to Know about Data Mining and Data-Analytic Thinking. United States, O'Reilly Media, 2013.
2. James, Gareth, et al. An Introduction to Statistical Learning: With Applications in Python. Germany, Springer International Publishing, 2023.
3. Shmueli, Galit, et al. Data Mining for Business Analytics: Concepts, Techniques, and Applications in R. Germany, Wiley, 2017.
4. Diez, David, et al. OpenIntro Statistics. United States, OpenIntro, Incorporated, 2019.
