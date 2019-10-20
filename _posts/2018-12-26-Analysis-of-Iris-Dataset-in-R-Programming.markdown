---
layout: post
title: Analysis of Iris Dataset in R Programming
date: 2018-12-26 13:32:20 +0300
description: Analysis of Iris Dataset in R Programming. # Add post description (optional)
img: Analysis-of-Iris-Dataset.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Iris Dataset, Data Science, Iris analysis, R Programming, Data Analyis]
---
First of all you need to install '[multigraph](https://www.rdocumentation.org/packages/multigraph/versions/0.91)' library if already not installed

* load 'multigraph' library

```R  
library(multigraph)
```


* Load Iris dataset as matrix in matrix variable

```R 
matrix <- data.matrix(iris)
```


* Matrix transpose because 'cor' method calculate column wise correlation

```R 
trn <- t(matrix)
```


* Calculate pairwise correlation (150*150) in pwcor variable

```R 
pwcor <- cor(trn)
```


* Save calculated (150*150) correlation in csv file

```R 
write.csv(pwcor, file = "correlation.csv")
```


* Define scope of node / edge / graph characteristics as list object

```R 
scp3 <- list(cex = 1, fsize = 3, pch = c(19, 15), lwd = 1.5, vcol = 2:3)
```


* Map pairwise correlation (150*150) to 'circ2' layout base graph

```R
bmgraph(pwcor, layout = "circ2", scope = scp3, main = "Iris correlation using bmgraph")
```

![Analysis of Iris Dataset in R Programming]({{site.baseurl}}/assets/img/posts/Analysis-of-Iris-Dataset.png)


* Calculate mean, median and summary

```R
mean(pwcor)
median(pwcor)
summary(pwcor)
```
DONE :)

Feel free to extend this post and don't forget to share with others ... :)