# Home-Credit-Default-Risk-Detection
Home Credit risk has been a prevalent concern in the housing sector for decades. Credit risk is defined as “the possibility of a loss resulting from a borrower’s failure to repay a loan or meet contractual obligations.” This risk is especially important in the housing and financial sector where a default can result in a financial institution not being paid back. That can result in the financial institution not being able to meet their own obligations or carry out their own operations. In addition to financial loss, defaults can also result in the financial institution not extending credit to other borrowers, which can have a broader impact on the economy.

Our team, , has acquired data about various credit cases from Kaggle, an online data science competition facilitator and data repository. 

# 1) ETL 
The first thing our team did was build an ETL pipeline before we could analyze our data. We began our data extraction by extracting our data from Kaggle. We used Google Colab as our development environment. 

We were able to load our data directly from Kaggle into Colab and unzip the files. Once we had access to our data in the form of a dataframe, we had to transform it into something usable. We had to merge several different data files in order to create one file to be used in our analysis. We also had to remove several outliers in various columns that did not make sense given our domain knowledge. 

The final step in our ETL process was to save our prepped data, to avoid having to prepare data every time we opened the notebook. We decided to save our data to Google Drive because it is free and promotes collaboration. This concluded our ETL process.   

# 2) Analysis
Once our data was properly merged and cleaned, we were able to begin our analysis. We ran several different models and compared the results in order to choose the best one. Since the data had 92% of non-defaulters’ applications and just 8% of defaulters’ applications, the baseline accuracy of our training set was initially 92%. After running logistic regression which predicts well with a linear boundary and random forest which uses a non-linear boundary, our accuracy never went past 63% and true positive rate was below 20%. Hence, we had to undersample the non-defaulters application records such that our training set had an proportionate number of defaulters and non-defaulters (60:40) application records and our test dataset had the extreme bias just like in the real world datasets. 

We then ran k-means clustering, logistic regression, deep neural network, random forest and xgboost model on our training set. Each model gave us a glimpse into the nature of our data. Initially, our assumption was that there were identifiable clusters within the data. Hence, we ran the K-Means algorithm on our data. However, the clusters obtained were not very homogenous, which led us to believe that the data was not easily separable between the two classes. This led us to run a logistic regression model. We then discovered that the data was not linearly separable even with the right class weights, and thus had to use algorithms which have a non-linear separable boundary. We confirmed this by running Principal Component Analysis on the training dataset. This led us to run a random forest model. Also, upon discovering how complicated this dataset was, we decided to try a more complex approach. We ran a deep neural network with convolutional and dense layers to improve our predictions. We understood that the deep neural network was not able to learn much although it gave good enough metrics. 

Finally, we decided to build upon our random forest model by using xgboost, which improved the model’s accuracy and gave us a very good true positive rate of 72.9% along with a decent accuracy of 69%. Surprisingly, these figures were very similar to that of the logistic regression model. We decided that we would use the xgboost model for future predictions because it’s less likely to overfit and does automatic feature selection. Correctly identifying the defaulters is the priority here, so it makes sense to use the true positive rate as our primary metric. 

# 3) Conclusion: 
Our analysis of this data has led us to several findings. 
The dataset we used was highly biased. 92% of the data was of non-defaulters applications. Defaulted transactions are rare given a large pool of transactions. Something interesting that we found in the data was that the source of the transaction had a lot of predictive power to determine whether or not the transaction was defaulted on or not.  This information can be used to predict defaults and therefore reduce the amount of defaults in an organization. 
Reducing the amount of defaults in an organization can benefit the employees,customers, constituents and every other stakeholder. Our results would be interesting to company executives who are interested in reducing the amount of defaults within their organization and to those who work within the government. It is essential that the government be able to maintain financial solvency. Preventing defaults is an important step in doing that.It holds especially true for the financial services industry. Banks need to prevent defaults so that they can remain solvent and properly handle withdrawals in order to prevent runs on the bank and maintain social order. 

In conclusion, default on home credit loans is a devastating problem that can wreak havoc on an organization’s customers, employees, profits, shareholders and stakeholders, as well as the general public. Our team has created an advanced analytics solution to assist organizations in detecting credit risk so that they can respond appropriately to it. This solution was created in Python with the goal of using machine learning to detect Home credit default risk. This credit risk can result in organizations having more engaged employees, more financially healthy customers and higher profits. This will improve the lives of employees, customers, shareholders and stakeholders.
