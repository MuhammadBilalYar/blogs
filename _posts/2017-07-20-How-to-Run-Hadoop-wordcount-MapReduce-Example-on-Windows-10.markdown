---
layout: post
title: How to Run Hadoop wordcount MapReduce on Windows 10
date: 2017-07-20 19:32:20 +0300
description: How to Run Hadoop wordcount MapReduce on Windows 10 # Add post description (optional)
img: hadoop/mapreduce.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [hadoop, Data Science, Data Analyis, mapreduce]
---
How to Run Hadoop wordcount MapReduce on Windows 10

## Prepare
1. Download MapReduceClient.jar (Link: https://github.com/MuhammadBilalYar/HADOOP-INSTALLATION-ON-WINDOW-10/blob/master/MapReduceClient.jar)

1. Download Input_file.txt (Link: https://github.com/MuhammadBilalYar/HADOOP-INSTALLATION-ON-WINDOW-10/blob/master/input_file.txt)

Place both files in "C:/"

## Hadoop Operation
1. Open cmd in Administrative mode and move to "C:/Hadoop-2.8.0/sbin" and start cluster 

```
Start-all.cmd
```

![start all]({{site.baseurl}}/assets/img/posts/MapReduce/start%20all.PNG)

2. Create an input directory in HDFS.

```
hadoop fs -mkdir /input_dir
```

3. Copy the input text file named input_file.txt in the input directory (input_dir)of HDFS.

```
hadoop fs -put C:/input_file.txt /input_dir
```

4. Verify input_file.txt available in HDFS input directory (input_dir).

```
hadoop fs -ls /input_dir/
```

![Input_file]({{site.baseurl}}/assets/img/posts/MapReduce/Capture.PNG)

5. Verify content of the copied file.

```
hadoop dfs -cat /input_dir/input_file.txt
```

![Content]({{site.baseurl}}/assets/img/posts/MapReduce/fileContent.PNG)

6. Run MapReduceClient.jar and also provide input and out directories.

```
hadoop jar C:/MapReduceClient.jar wordcount /input_dir /output_dir
```

![Success]({{site.baseurl}}/assets/img/posts/MapReduce/Success.PNG)

7. Verify content for generated output file.

```
hadoop dfs -cat /output_dir/*
```

![out]({{site.baseurl}}/assets/img/posts/MapReduce/output.PNG)

### Some Other usefull commands
To leave Safe mode

```
hadoop dfsadmin –safemode leave
```

To Delete file from HDFS directory

```
hadoop fs -rm -r /iutput_dir/input_file.txt
```

To Delete directory from HDFS directory

```
hadoop fs -rm -r /iutput_dir
```

![comm]({{site.baseurl}}/assets/img/posts/MapReduce/command.PNG)