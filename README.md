# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary packages using import statement.
2. Read the given csv file using read_csv() method and print the number of contents to bedisplayed using df.head().
3. Import KMeans and use for loop to cluster the data.
4. Predict the cluster and plot data graphs.
5. Print the outputs and end the program


## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Subhash V
RegisterNumber:  212224240163
*/
```python
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv(r"C:\Users\acer\Downloads\Mall_Customers.csv")
data.head()

```
<img width="1035" height="306" alt="Screenshot 2026-05-20 154045" src="https://github.com/user-attachments/assets/52a56d5d-df95-4e7a-ab26-32b9d3248743" />

```python
data.info()
```

<img width="1117" height="425" alt="Screenshot 2026-05-20 154057" src="https://github.com/user-attachments/assets/739d9587-5bb1-4640-be8d-56320c7f8144" />

```python
data.isnull()
```

<img width="1121" height="575" alt="Screenshot 2026-05-20 154113" src="https://github.com/user-attachments/assets/1cf94bc3-bda7-4bcc-9fa2-f2a93ffef912" />

```python
data.isnull().sum()
```
<img width="867" height="282" alt="Screenshot 2026-05-20 154121" src="https://github.com/user-attachments/assets/41abfe3f-83a8-4a34-a631-1aa1bd18c165" />

```python
from sklearn.cluster import KMeans
wcss= [] 
for i in range(1,11):
    kmeans=KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```
<img width="1126" height="737" alt="Screenshot 2026-05-20 154137" src="https://github.com/user-attachments/assets/e2154c5b-7895-444e-8187-73f8e0f0756d" />

```python
km=KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
```

<img width="1117" height="307" alt="Screenshot 2026-05-20 154149" src="https://github.com/user-attachments/assets/055abe00-a228-4462-afb1-93024c57d4d5" />

```python
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="black",label="cluster")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="cyan",label="cluster")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="yellow",label="cluster")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="blue",label="cluster")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="green",label="cluster")
plt.legend()
plt.title("Customer Segments")
```

<img width="1107" height="775" alt="Screenshot 2026-05-20 154203" src="https://github.com/user-attachments/assets/cd10216c-4f58-429e-a8c9-447b19a23185" />




## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
