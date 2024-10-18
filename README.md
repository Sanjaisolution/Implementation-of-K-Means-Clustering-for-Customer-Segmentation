![image](https://github.com/user-attachments/assets/65dcb997-06c5-4554-98d3-ac204294a46d)# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
Step 1. Start the program

Step 2. Import the necessary python libraries

Step 3. Read the dataset of Mall_Customers csv file

Step 4. From sklearn libraary select the cluster and import KMeans Clustering

Step 5. Find the sum of squared distance between each points and the centroid in a cluster using Elbow Method

Step 6. Plot the graph x and y as Number of Clusters and wcss respectively

Step 7. Using the matplotlib library draw the scatter plot for the given number of clusters (ie. here n_clusters = 5)

Step 8. Stop the program

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Sanjai.R
RegisterNumber:  212223040180
*/
```
```py
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
```

## Output:
![Screenshot 2024-10-18 223943](https://github.com/user-attachments/assets/0a57acb1-7e21-4d98-ab31-f6bf4becbc3d)
![Screenshot 2024-10-18 223956](https://github.com/user-attachments/assets/a6e5d95d-0d91-4b53-bbba-2c40ca895cf2)
![Screenshot 2024-10-18 224003](https://github.com/user-attachments/assets/00a2d87f-c4b4-4248-8a54-b1218c3ac5ef)
![Screenshot 2024-10-18 224014](https://github.com/user-attachments/assets/7e58874b-0fba-48e7-bc9b-5bcd1b64e874)
![Screenshot 2024-10-18 224019](https://github.com/user-attachments/assets/a1273fc7-d268-4af9-b169-64485685de68)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
