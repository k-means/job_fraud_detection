# Job Fraud Prediction.
#### A project by Team K-Means


Most modern organisations use the web and social media platforms for employee recruitment and job opening advertisements. In recent years, many companies prefer to post their vacancies online so that they can be accessed easily and quickly by interested job-seekers.The number of job seekers who search online for employment opportunities has in effect increased exponentially. Unfortunately, with this trend comes the opportunity for criminals to exploit job seekers with fake job offers as a way to extract personal information to be used in nefarious activities. Thus, a system for detecting fraudulent job postings is necessary for both the credibility of Job posting sites or companies and also for the safety of job seekers. 
By applying machine learning techniques, we can help job seekers detect job ads that are fraudulent and deploy a job recommendation system.


## The Dataset
For this project, a raw dataset containing fraudulent and real jobs from about 17880 job posting observations was used. The (dataset)[https://www.kaggle.com/subhajournal/job-fraud-detection] was obtained from (kaggle)[www.kaggle.com]
Full URL: https://www.kaggle.com/subhajournal/job-fraud-detection
This dataset displays the different types of jobs, their location, salary range, job descriptions and roles. 


## Data Exploration
The dataset consisted of 17,880 observations and 16 features.The data was a combination of integer and string data types. The dataset was made up of some features with a lot of null values and some with little or no null values. A 60% threshold for null values was used to identify the columns that were dropped from the dataset.

<p align="center">
  <img 
    alt = "Data Exploration"
    src="https://github.com/uzoochogu/job_fraud_detection/blob/main/images/Data%20Exploration.png"
  >
</p>



## Exploratory Data Analysis
In order to better understand the data and get information from the dataset used, some exploratory data analysis was carried out.

### Job Location
As seen below, the Location with the most count in the dataset is GB, London and the follow up location is US, New York. The other top 8 can be observed in the chart below.

<p align="center">
  <img 
    alt = "Top 10 Job Location"
    src="https://github.com/uzoochogu/job_fraud_detection/blob/main/images/Top%2010%20Job%20Location.png"
  >
</p>


### Experience/Type of Employment
A countplot was also obtained from the Experience and Type_of_Employment columns as shown below. The most occurring category in the Experience column was the ”Not stated” followed by “Mid-Senior level”. It was also observed that the most occurring jobs were full time roles.
The Job advertisements with no experience stated in them were shown to be most likely to contain Fraudulent jobs than any other category.

<p align="center">
  <img 
    alt = "Type of Employement Job Count"
    src="https://github.com/uzoochogu/job_fraud_detection/blob/main/images/Type%20of%20Employment%20Job%20Count.png"
  >
</p>

<p align="center">
  <img 
    alt = "Experience Fake Job count"
    src="https://github.com/uzoochogu/job_fraud_detection/blob/main/images/Experience%20Fake%20Job%20Count.png"
  >
</p>



### Job Title

The plot above shows that titles like “Customer Service Representative” and “Administrative Assistant” contained the most number of fake job advertisements.

<p align="center">
  <img 
    alt = "Job Title fake job count plot"
    src="https://github.com/uzoochogu/job_fraud_detection/blob/main/images/Job%20Title%20fake%20job%20count%20plot.png"
  >
</p>



### Qualification
We can see that the Qualification column also has most of the fake job ads where the required qualifications were not stated.

<p align="center">
  <img 
    alt = "Qualification Countplot"
    src="https://github.com/uzoochogu/job_fraud_detection/blob/main/images/Qualification%20Countplot.png"
  >
</p>



### Range of Salary
It was found out that 85% of the jobs in the dataset had no salary range provided or they were unpaid jobs. 86% of the real jobs had no salary range and 75% of the fake jobs had no salary range.

<p align="center">
  <img 
    alt = "Box Plot"
    src="https://github.com/uzoochogu/job_fraud_detection/blob/main/images/Box%20Plot%20Non%20Zero%20Salary.png"
  >
</p>

The histogram revealed similar distributions for the real and fake jobs postings. The boxplot is slightly more revealing, the real jobs had a greater spread than the fake ones, but the medians were about the same (although, it's difficult to believe that the mean salary was around $10,000).


<p> </p>

## Data Preprocessing
The preprocessing stage for our data was very straightforward since we had a majority of text columns.They include the following:

- Null value Imputation
- Feature combination
- Data Cleaning: Lowering, Tokenization, stopwords removal, e.t.c
- Feature extraction with Tfidf vectorizer
- Oversampling to Handle Class Imbalance

We then generated a correlation matrix to see the importance of the numerical features. The matrix is shown below:

<p align="center">
  <img 
    alt = "Correlation Matrix"
    src="https://github.com/uzoochogu/job_fraud_detection/blob/main/images/Correlation%20Matrix.png"
  >
</p>


The matrix indicated that the numerical features had very low correlation with the target Fraudulent feature. Therefore, we dropped the numerical features and focused on the text feature we had cleaned.





## Modelling
### Model Selection
A total of 9 models were trained on the vectorized data and the best three performing models were fine tuned using grid search before selecting the best performing model. A passive aggressive classifier showed the best performance on the test set and was therefore selected.
### Metrics and Model Evaluation
The model was evaluated primarily using three evaluation metrics. Precision, recall and F1 score. The F1 score was used as the most important metric since it was a combination of precision and recall and the result we obtained can be seen in the image below.
### Model Deployment
The model was deployed using streamlit after the vectorizer and the trained model were pickled. These pickled files were used in the deployment to classify text inputs that contained details of the Job being advertised.


<p align="center">
  <img 
    alt = "Deployed Model"
    src="https://github.com/uzoochogu/job_fraud_detection/blob/main/images/Deployed%20Model.png"
  >
</p>
