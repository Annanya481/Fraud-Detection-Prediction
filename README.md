# Fraud-Detection-Prediction

## Problem Statement
The following is a machine learning model to detect and predict the occurrence of fraudulent transactions on the basis of the following factors:
* Step (a unit of time in the real world, in this case 1 step is 1 hour of time)
* Type of transaction
* Amount of transaction
* Name of originator of transaction
* Initial balance of originator
* Final balance of originator
* Initial balance of recipient 
* Final balance of recipient
* Name of recipient
* isFraud (This is the transactions made by the fraudulent agents inside the simulation. In this specific dataset the fraudulent behavior of the agents aims to profit by taking control or customers accounts and try to empty the funds by transferring to another account and then cashing out of the system.)
* isFlaggedFraud (The business model aims to control massive transfers from one account to another and flags illegal attempts. An illegal attempt in this dataset is an attempt to transfer more than 200.000 in a single transaction.)

The dataset can be found [here](https://drive.google.com/uc?id=1BiTEaQ6MM3OXku8EhDoCa9EGhHmIuCGM&export=download).
## Working Methodology 

![image](https://user-images.githubusercontent.com/60508605/174591081-2591b066-c378-4231-b816-2d2a1d3fa588.png)

### Data Cleaning 
Data cleaning involves checking for NULL values, removing missing columns with missing values, etc.

### Exploratory Data Analysis
Distribution on the basis of type of transactions is as follows. CASH_OUT and TRANSFER are the top two types with ~35%.
![image](https://user-images.githubusercontent.com/60508605/174591933-1a6c9f6b-65c1-427a-a8a4-c527ab6a11fe.png)

75% of the data falls under amount 208722, but the maximum amount being 92445517 which is pretty large, as also can be seen in the graph. 
There are a lot of extreme outliers present in this data.
![image](https://user-images.githubusercontent.com/60508605/174592017-e4b75618-df42-4820-a8ea-c3bc2e4940cb.png)

This is a highly skewed data, only 0.1% of the transactions are fraudulent.
![image](https://user-images.githubusercontent.com/60508605/174592063-68e22268-1c57-407b-a055-199e471cff80.png)

As we can see, amounts in fraudulent transactions varies from 0 to 107, with an mean of around 14,67,968. But the current model only flagged transactions having very high amounts, with a minimum amount of 3,53,874.
![image](https://user-images.githubusercontent.com/60508605/174592120-a19a40b6-86d1-4704-ae00-ade9d4237a53.png)

Since, only types CASH_OUT and TRANSFER have frauds, so the following plots consists of transactions and frauds from these 2 types only. As we can see, number of CASH_OUT and TRANSFER transactions varies a lot in the whole month, i.e. low in the first week, high in middle and again fairly low towards the end. 
![image](https://user-images.githubusercontent.com/60508605/174592204-5ebe974c-5d03-47c2-a4f2-3b4fb46e6425.png)

So, on an average 7.4% of the transactions are fraudulent per day, which is little high due to the presence of high frauds percentage on days 3rd and 31st. These 2 days are clear outliers for this month.
![image](https://user-images.githubusercontent.com/60508605/174593013-9c51432e-f3c5-4316-acf2-f9c95d7c1699.png)

### Model Training and Prediction
The models used are Logistic Regression and Random Forest.

#### Logistic Regression
Logistic regression is a process of modeling the probability of a discrete outcome given an input variable. The confusion matrix is plotted as below

![image](https://user-images.githubusercontent.com/60508605/174593549-40342ddf-09cd-41f3-8e09-e64d91690b4e.png)

#### Random Forest
Random Forest Regression is a supervised learning algorithm that uses ensemble learning method for regression. Ensemble learning method is a technique that combines predictions from multiple machine learning algorithms to make a more accurate prediction than a single model. The confusion matrix is plotted as below

![image](https://user-images.githubusercontent.com/60508605/174593652-65567bfc-a232-4d3e-a1c1-4977698b49da.png)
