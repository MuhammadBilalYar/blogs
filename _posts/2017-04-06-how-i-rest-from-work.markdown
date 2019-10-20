---
layout: post
title: Analysis of Iris Dataset in R Programming
date: 2018-12-26 13:32:20 +0300
description: Analysis of Iris Dataset in R Programming. # Add post description (optional)
img: Analysis-of-Iris-Dataset.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Iris Dataset, Data Science, Iris analysis, R Programming, Data Analyis]
---
First of you need to install 'multigraph' library if already not installed

* load 'multigraph' library

<pre> library(multigraph)</pre>

* Load Iris dataset as matrix in matrix variable
<pre>matrix <- data.matrix(iris)</pre>

* Matrix transpose because 'cor' method calculate column wise correlation
<pre>trn <- t(matrix)</pre>

* calculate pairwise correlation (150*150) in pwcor variable
<pre>pwcor <- cor(trn)</pre>

* save calculated (150*150) correlation in csv file
<pre>write.csv(pwcor, file = "correlation.csv")</pre>

* define scope of node / edge / graph characteristics as list object
<pre>scp3 <- list(cex = 1, fsize = 3, pch = c(19, 15), lwd = 1.5, vcol = 2:3)</pre>

* Map pairwise correlation (150*150) to 'circ2' layout base graph
```ruby
bmgraph(pwcor, layout = "circ2", scope = scp3, main = "Iris correlation using bmgraph")
```