# Udacity Datascience Capstone Project

**Table of Contents**
1.	Installation
2.	Project Motivation
3.	File Descriptions
4.	Results
5.	Licensing, Authors, and Acknowledgements

# Installation
Anaconda Navigator V.1.10.0 was utilised, with the code being written using Jupyter Notebook V.6.1.4. Python version 3 was used. Standard packages such as Pandas, numpy and datetime were installed. For creating charts matplotlib and seaborn were installed. Several packages from Sklearn were utilised for modelling. These included, from metrics: classification_report and confusion_matrix. From Model_selection: train_test_split and GridSearchCV as well as classifiers LogisticRegression and RandomForestClassifier.

# Project Motivation

This project is the capstone project of the Udacity Data Science Nanodegree. The aim of the project selected was to determine which demographic groups respond best to which offer type using simulation data provided by Starbucks. 

Customers can register to become a member of Starbucks, and consequently be sent a variety of different promotional offers. When received by the customer some will view the offer whilst others will not. Customers can then go on to ‘complete’ the offer providing it is utilised within the validity time period. However it is also possible for a customer to have completed an offer, but not received or viewed the promotion.

Offers provided to customers could range from promotional and informational offers to ‘Buy one get one free’ (BOGO) as well as Discounts. Each offer has a set ‘difficulty’, ‘reward’ and ‘duration’. These represent the cost that the monies the customer must spend to utilise the offer, the discount or reward received from utilising the offer, as well as the period of time that the offer is valid for

For this project I chose two primary questions: The first is regarding which customers respond best to which offers. For the second, accepting that there are customers that can complete an offer without having viewed of received an offer, the focus will instead refined to consider the population of customers that complete and offer having viewed them. Consequently, the questions of interest in this project were:

1.	What demographics respond best to offers?
2.	Is it possible to predict if a customer will complete an offer once it is viewed?

In answering these questions offers could become more targeted to maximise sales with Starbucks and number of customers completing offers when they are issued.

# File Descriptions
There is only one notebook for this analysis, it is a self-contained notebook which will produce the output for each of the 2 stated questions. The notebook has been separated into sections.
There were 3 datasets provided: Profile, Transcript and Portfolio. Files were provided as .json which were then imported to a Jupyter notebook. A brief description of each file is below:

**Portfolio**: The portfolio file contains information regarding the type of offers. In total there are 10 offers provided by Starbucks, each with a different level of difficulty, reward and duration of offer. There are 10 rows and 6 columns in this file. For each offer a unique offer code is present – this can be used to link to the transcript file. The offer_type variable contains a label description of the offer, for instance: ‘BOGO’ for ‘Buy one get one free’ and ‘Discount’.  The ‘Reward’, ‘Duration’ and ‘Difficulty’ of the offer were captured in fields named the same. Additionally, the channel which the offer is available on is held as a list within the ‘Channel’ field.

**Profile**: The profile dataset contained information about Starbucks’ members, and has 17,000 rows and 5 columns. Within the data is was an ‘id’ variable, representing the customer. Within the dataset there is information on the customer’s ‘Age’, ‘Income’ and ‘Gender’. In addition there was a field representing the date when the customer became a Starbucks member. 

**Transcript:** There were 306,534 rows in this file representing different stages of an offer cycle as well as if a transaction was made. There were 4 columns in this dataset. The ‘event’ field captures the stages of the offer, and is made up of 4 levels (offer received, offer viewed, offer complete and transaction). The dataset also contains a field called ‘value’. The data within each cell of the frame for this field are held within a dictionary. The contents of the dictionary are either the unique id for the offer that was sent to the customer, or the amount of money that the customer transacted with Starbucks. ‘Time’, is a marker measured in hours for when an activity occurred. For every customer, time starts at 0 and each time an offer is received, viewed, completed or a transaction is made the ‘time’ variable captures the number of hours since the start that this activity occurred. A unique id, referred to as ‘person’ was within the data, this was used to join to the profile information.

# Results

In answering the question, 'Is it possible to predict if a customer will complete an offer once it is viewed?' two models were chosen. The first was an initial Baseline model using Logistic Regression, with the second being a Random Forest. An initial baseline Logistic Regression model was created which resulted in an accuracy score of 0.58, with an average F1-score of 0.58. This model also had an AUC of 0.62.

The Random Forest model with 150 estimators performed best, producing an accuracy score of 0.75 AUC of 0.83 and F1 score of 0.76. The model has a good ability to separate between classes. The model outputs also highlighted key features of importance. It was shown that 'Tenure' and 'cum_offer_amt' as being the top two features in determining whether or not a customer will complete an offer once it is viewed. From the exploratory analysis it was shown that customers that have a greater tenure tend to complete offers. Also, those that have a greater cumulative amount of spend with Starbucks prior to an offer being issued tend to complete offers once they are viewed. This suggest some aspect of brand loyalty.

The main findings however, can be found at the following Medium post.


# Licensing, Authors, Acknowledgements
Data was provided by Starbucks as part of the Udacity Data Science Nanodegree capstone project. Thanks for an interesting project.

Seaborn’s Histplot would not run within the Udacity classroom, Stackoverflow suggested using pip3 to install the package then restart the Kernel. Thanks to the author at the Stackoverflow link that provided this [solution](https://stackoverflow.com/questions/64815227/attributeerror-module-seaborn-has-no-attribute-histplot?rq=1).

Additionally, the code to create the feature importance chart was provided from a post at Stackoverflow, and amended so that it could be incorporated into this project. Thanks to the author that provided this [solution](https://stackoverflow.com/questions/44101458/random-forest-feature-importance-chart-using-python).
