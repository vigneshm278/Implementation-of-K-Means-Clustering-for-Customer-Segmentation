# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
step 1. Start the program

step 2. Import the necessary python libraries

step 3. Read the dataset of Mall_Customers csv file

step 4. From sklearn libraary select the cluster and import KMeans Clustering

step 5. Find the sum of squared distance between each points and the centroid in a cluster using Elbow Method

step 6. Plot the graph x and y as Number of Clusters and wcss respectively

step 7. Using the matplotlib library draw the scatter plot for the given number of clusters (ie. here n_clusters = 5)

step 8. Stop the program

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: YUVARAJ V
RegisterNumber: 212223230252
*/

import pandas as pd
import matplotlb.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")

data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
  kmeans = KMeans(n_clusters = i,init = "k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
data["cluster"] = y_pred

df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="olive",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="orange",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
### Elbow Method
![image](https://github.com/user-attachments/assets/4b5b7e98-9b0d-4d96-93ba-6774e363633a)

### Y Prediction
![image](https://github.com/user-attachments/assets/8f6822f8-f92c-429e-b892-841752b94ed2)

### Customer Segmentation
![image](https://github.com/user-attachments/assets/d12d92ba-e0ed-4ab9-b477-335973fe8560)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
