# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import dataset and print head,info of the dataset
2.check for null values
3.Import kmeans and fit it to the dataset
4.Plot the graph using elbow method
5.Print the predicted array
6.Plot the customer segments

## Program:
```python

#Program to implement the K Means Clustering for Customer Segmentation.
#Developed by: Sanjeev
#RegisterNumber: 212224230246


import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("/content/drive/MyDrive/Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
  kmeans = KMeans(n_clusters = i, init = "k-means++")
  kmeans.fit(data.iloc[:, 3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])
y_pred = km.predict(data.iloc[:, 3:])
y_pred
data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c = "red", label = "cluster0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c = "black", label = "cluster1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c = "blue", label = "cluster2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c = "green", label = "cluster3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c = "magenta", label = "cluster4")
plt.legend()
plt.title("Customer Segments")



```

## Output:


![image](https://github.com/user-attachments/assets/f6d54232-83c0-4db9-8c3f-d20108a50d2d)
![image](https://github.com/user-attachments/assets/38a93033-40c4-4e86-bfd9-ee3e138b3a6a)
![Screenshot 2025-05-14 132756](https://github.com/user-attachments/assets/4de892b3-61c0-4bbb-aa3d-a1f3c272eb82)
![Screenshot 2025-05-14 132740](https://github.com/user-attachments/assets/0354e750-0caa-40c6-bc0c-f2483f081206)
![Screenshot 2025-05-14 132733](https://github.com/user-attachments/assets/1a6d3330-236e-49f5-a433-2a28fce1140a)
![Screenshot 2025-05-14 132728](https://github.com/user-attachments/assets/25e3c0be-a621-4685-a150-bd8c43a98c20)
![Screenshot 2025-05-14 132710](https://github.com/user-attachments/assets/305f61b8-15a0-4a0f-8f9a-f4f265cc8ce9)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
