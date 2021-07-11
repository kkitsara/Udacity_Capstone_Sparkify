In this folder you may find the below files.

README.md - The file that explains the repository purpose and structure

LICENSE - The license file

Sparkify.ipynb - The notebook that hosts the data analysis and the ML model build and test

mini_sparkify_event_data.7z - The subset of the data used for the analysis that is a zipped json

Folder /try_runs/ - It accomodates the test codes where we executed the different tests with the different lists of predictors until we find the final one.
The folder inside contains the Jupyter notebooks of the test runs with the name format Sparkify_X_run.ipynb

summary of the project! 

The purpose of this project is to build an ML model that predicts the churn scoring for the users of a music streaming platform called Sparkify.
Sparkify gives to the users the capability to exlore through it and stream various songs of various artists.
There are 2 different type of users in Sparkify:

1. Users that can browse through the songs and all the functionalities but they are served adverts frequently. These are the Free layer users.
2. Users that can browse through the full functionalities songs without any adverts. These are the Paid layer users.

As churn users in Sparkify, we consider the ones that move from Paid layer to Free layer or move from Free layer to no layer at all.
It is very important to identify the users with high propensity of leaving Sparkify, as these customers may lead to loss of big revenues for Sparkify.
In general for all the compaines, the churn analysis is a very important process, as identifying early potential churners, could lead to marketing and promo
activities on them in order to increase the revenues and the loyalty.

The goal of this project is predict the churn score of the users that use the platform. 
The data we are using on this project are the events data of all the users. 
The events data give for each user the info of the page visited, the song listened and other characteristics related to the user (eg. name,gender),
the song (eg name,artist) and the event (eg. timestamp, page type, browser details)

For example if one user listened 5 songs and went once to the settings page, we will have 5 records with page type song and 1 record with page type settings.

The project is written in pyspark, as this was a dependency. Spark is a multithread processing tool, that is suitable for big data.
The initial full dataset has size 12GB, but in the notebook above we work on a subset file of the same structure and size 128MB.
The goal is the code to be scalable and can be used, as is, even with the 12GB dataset, of course in a cluster that provides the relevant capacity and power.

Tje jupyter notebook contains 5 main sessions explained below:

1. Import of Libraries and Build of Spark Session

2. Load and Clear the Dataset:
   - On this session we read the json file, convert it to spark dataframe and perform a first analysis in the data trying to understand the basic concepts,
   finding missing entries and other issues and fixing them

3. Exploratory Data Analysis
   - On this session we perform a further analysis more in depth and we proceed in the transformation of the dataset, by changing accordingly some columns.
   We try to understand the concept of churn in the data and we create a new characteristic for the users, if they have performed a churn or not
   
4. Feature Engineering
   - On this session we perform an even deeper analysis and the transformation of the dataset. The goal is to create the dataset that will be used as an input
   in the ML model. We want to create a dataset containing unique records per user and a batch of KPIs that depict properly their characteristics and their behavior.
   We try also to understand using visualization techniques which of these KPIs could be significant for our ML model.
   
5. Modeling
   - On this session we execute the ML Model. 
   First of all, we try to apply scalability techniques, by converting the KPIs to vectors and then scaling them properly.
   Then we create the features and the label objects that will be used as input in the ML algorithms.
   Then we split the data into train and test datasets
   Then we perform the training and test of 4 different ML classification algorithms GBT, Random Forest, Logistic Regression and SVM
   Then we evaluate them and compare the results
   
   We perform all the above steps with several different combinations of interesting KPIs, we store the results and eventualy we choose the best algorythm and the
   best data to execute the classification.

Ideally the next step would be to run the same code for the full dataset in a proper Spark cluster and evaluate the results with the full dataset.
If the results are satisfying, we can create the pickle file and apply in another code the calculation of the churn scoring for all the users.
The users with high churn score are more risky to leave the Sparkify platform and generate loss of revenues, so we should target them with offers and gifts,
in order convince them stay in the platform and increase their loyalty.