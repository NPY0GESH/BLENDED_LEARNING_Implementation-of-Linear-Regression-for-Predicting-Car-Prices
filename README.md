# BLENDED_LEARNING
# Implementation-of-Linear-Regression-for-Predicting-Car-Prices
## AIM:
To write a program to predict car prices using a linear regression model and test the assumptions for linear regression.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
Import Libraries: Bring in essential libraries such as pandas, numpy, matplotlib, and sklearn.

Load Dataset: Import the dataset containing car prices along with relevant features.

Data Preprocessing: Manage missing data and select key features for the model, if required.

Split Data: Divide the dataset into training and testing subsets.

Train Model: Build a linear regression model and train it using the training data.

Make Predictions: Apply the model to predict outcomes for the test set.

Evaluate Model: Measure the model's performance using metrics like R² score, Mean Absolute Error (MAE), etc.

Check Assumptions: Plot residuals to verify assumptions like homoscedasticity, normality, and linearity.

Output Results: Present the predictions and evaluation metrics.

## Program:
```
/*
 Program to implement linear regression model for predicting car prices and test assumptions.
Developed by: N.P.YOGESH
RegisterNumber:

import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error,r2_score,mean_absolute_error
from sklearn.preprocessing import StandardScaler
import matplotlib.pyplot as plt
import seaborn as sns
import statsmodels.api as sm

x=df[['enginesize','horsepower','citympg','highwaympg']]
y=df['price']

#split data
x_train,x_test,y_train,y_test=train_test_split(x,y,test_size=0.2,random_state=42)

#feature scaling
scaler=StandardScaler()
x_train_scaled=scaler.fit_transform(x_train)
x_test_scaled=scaler.transform(x_test)

#training model
model=LinearRegression()
model.fit(x_train_scaled,y_train)
#prediction
y_pred=model.predict(x_test_scaled)

#Model coefficients and metrics
print('Name:N.P,YOGESH')
print('Reg No:212225240189')
print('MODEL COEFFICIENTS:')
for feature,coef in zip(x.columns,model.coef_):
    print(feature,coef)
print(f"Intercept: {model.intercept_}")

print("\nMODEL PERFORMANCE")
print('MSE',mean_squared_error(y_test,y_pred))
print('RSME',np.sqrt(mean_squared_error(y_test,y_pred)))
print('MAE',mean_absolute_error(y_test,y_pred))
print('R-squared',r2_score(y_test,y_pred))

#Linearity check
plt.figure(figsize=(10,5))
plt.scatter(y_test,y_pred,alpha=0.6)
plt.plot([y.min(),y.max()],[y.min(),y.max()],'r--')
plt.title("Linearity Check:Actual vs Predicted prices")
plt.xlabel("Predicted Price($)")
plt.ylabel("Residuals($)")
plt.grid(True)
plt.show

#Independence (Durbin-watson)
residuals=y_test-y_pred
dw_test=sm.stats.durbin_watson(residuals)
print(f"\nDurbin-Watson Statistic: {dw_test:2f}",
     "\nValues close to 2 indicates no autocorrelation")

#Homoscedasity
plt.figure(figsize=(10,5))
sns.residplot(x=y_pred,y=residuals,lowess=True,line_kws={'color':'red'})
plt.title("Homoscedasticity Check:Residuals vs Predicted")
plt.xlabel('Predicted price ($)')
plt.ylabel('Residuals($)')
plt.grid(True)
plt.show()

#Normality of residuals
fig,(ax1,ax2)=plt.subplots(1,2,figsize=(12,5))
sns.histplot(residuals,kde=True,ax=ax1)
ax1.set_title("Resdiduals Distribution")
sm.qqplot(residuals,line='45',fit=True,ax=ax2)
ax2.set_title("Q-Q plot")
plt.tight_layout()
plt.show()


*/
```

## Output:
![simple linear regression model for predicting the marks scored](sam.png)
<img width="1405" height="667" alt="image" src="https://github.com/user-attachments/assets/2aa9fe7c-9a0c-4f81-a793-eabc1fe9af26" />
<img width="1811" height="827" alt="image" src="https://github.com/user-attachments/assets/c9509fdb-9d35-4414-b4da-41a303eea550" />
<img width="1906" height="850" alt="image" src="https://github.com/user-attachments/assets/e72abd13-c6c6-45d4-b0c4-6f8f5ec1647a" />


## Result:
Thus, the program to implement a linear regression model for predicting car prices is written and verified using Python programming, along with the testing of key assumptions for linear regression.
