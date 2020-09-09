# ACM Research Coding Challenge (Fall 2020)

## No Collaboration Policy

**You may not collaborate with anyone on this challenge.** You _are_ allowed to use Internet documentation. If you _do_ use existing code (either from Github, Stack Overflow, or other sources), **please cite your sources in the README**.

## Submission Procedure

Please follow the below instructions on how to submit your answers.

1. Create a **public** fork of this repo and name it `ACM-Research-Coding-Challenge`. To fork this repo, click the button on the top right and click the "Fork" button.
2. Clone the fork of the repo to your computer using . `git clone [the URL of your clone]`. You may need to install Git for this (Google it).
3. Complete the Challenge based on the instructions below.
4. Email the link of your repo to research@acmutd.co with the same email you used to submit your application. Be sure to include your name in the email.

## Question One

![Image of Cluster Plot](ClusterPlot.png)
<br/>
Given the following dataset in `ClusterPlot.csv`, determine the number of clusters by using any clustering algorithm. **You're allowed to use any Python library you want to implement this**, just document which ones you used in this README file. Try to complete this as soon as possible.

Regardless if you can or cannot answer the question, provide a short explanation of how you got your solution or how you think it can be solved in your README.md file.

Answer to Question 1: 

Name: Kokil Kounder 
Student ID: Krk190003
Utdallasemail: Krk190003@utdallas.edu 

Code: 
```
import csv
from sklearn.cluster import KMeans

f = open('ClusterPlot.csv', 'r')
reader = csv.reader(f)
next(reader)

def findNumClusters(Elbwlist):
    numclusters = 0
    difference = 0
    for i in range(1, len(Elbwlist)):
        diff = int(Elbwlist[i-1] - Elbwlist[i])
        if(diff > difference):
            difference = diff
            numclusters += i+1
    return("There are " + str(numclusters) + " clusters in this data set")

v3Coord = []
for row in reader:
    v3Coord.append([row[1],row[2]])

distortions = []

for i in range(1, 11):
    KM = KMeans(n_clusters=i, max_iter=500)
    KM.fit(v3Coord)
    distortions.append(KM.inertia_)
print(findNumClusters(distortions))

```




Explanation: 

I decided to use the K Means Clustering algorithim to figure out how many clusters there are in the above data set. Using the CSV library in python I was able to read the data given in ClusterPlot.csv file, and with the use of for loops I entered that data into a 2D List. Next I Imported the Kmeans Library from the sklearn.cluster directory, and created a forloop that would create 10 different Kmeans objects each with a different number of clusters, from (1-10). I then used the fit function to pass the values from ClusterPlot.csv into each Kmeans object, followed by the intertia method to find the distorition values for each kmeans object. I then stored them all in a 1D list called distortions. Finally I created a method called num clusters which would find the optimum K value (The value that would be the ideal # of clusters in a given data set) using the elbow method, and called it in a print statment using distortions as my parameter. To get the output: "There are 2 Clusters in this data set".

 
 Other Info: 
 
Used PyCharm IDE to code my program 
Used the following Libraries/Imports: 
  1. CSV: Used so python could have the ability to read a CSV file 
  2. Kmeans from sklearn.cluster: Used to make it easier and more effiecient to calclate the distrotions for many cluster values 
  
  Sources: 
  edureka! “K Means Clustering Algorithm | K Means Example in Python | Machine Learning Algorithms | Edureka.” YouTube, uploaded by edureka, 28 May 2018, www.youtube.com/watch?v=1XqG0kaJVHY&t=1456s. 
 
 “Elbow Method for Optimal Value of k in KMeans.” GeeksforGeeks, www.geeksforgeeks.org/elbow-method-for-optimal-value-of-k-in-kmeans. Accessed 8 Sept. 2020.

