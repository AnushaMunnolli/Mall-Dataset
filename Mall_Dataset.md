---
title: "Untitled"
author: "Anusha Vijaykumar Munnolli"
date: "May 29, 2018"
output: 
  html_document: 
    keep_md: yes
---

```r
getwd()
```

```
## [1] "C:/Users/Anusha Munnolli/Documents/R Programming Files/R MarkDown Files/K-Means_Clustering"
```

```r
setwd("C:\\Users\\Anusha Munnolli\\Documents\\MachineLearning\\Machine Learning A-Z Template Folder\\Part 4 - Clustering\\Section 24 - K-Means Clustering")
dataset <- read.csv('Mall_Customers.csv')
X <- dataset[,4:5]

#Determining the optimal number of clusters using the elbow method
set.seed(6)
wcss <- vector()
for(i in 1:10) wcss[i] <- sum(kmeans(X, i)$withinss)
plot(1:10, wcss,type = 'b', main= paste('K-means - Income Vs Spending'))
```

![](Mall_Dataset_files/figure-html/unnamed-chunk-1-1.png)<!-- -->

```r
#Applying k-means to the mall dataset 
set.seed(29)
kmeans <- kmeans( X, 5, iter.max = 300, nstart = 10)

#Visualizing the clusters 
library(cluster)
clusplot(X, 
          clus = kmeans$cluster,
          lines = 0,
          shade = TRUE,
          color = TRUE,
          labels = 2,
          plotchar = FALSE,
          span = TRUE,
          main= paste('Number of Clusters'),
          xlab= 'Annual Income', ylab = 'Spending Score')
```

![](Mall_Dataset_files/figure-html/unnamed-chunk-1-2.png)<!-- -->
