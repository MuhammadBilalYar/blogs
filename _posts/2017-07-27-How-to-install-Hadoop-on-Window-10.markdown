---
layout: post
title: Step by step Hadoop 2.8.0 installation on Window 10
date: 2017-07-27 9:32:20 +0300
description: Step by step Hadoop 2.8.0 installation on Window 10 # Add post description (optional)
img: hadoop/Hadoop-On-Window.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [hadoop, Data Science, Data Analyis]
---
Step by step Hadoop 2.8.0 installation on Window 10

## Prepare:
These softwares should be prepared to install Hadoop 2.8.0 on window 10 64bit

1. Download Hadoop 2.8.0 ([Link 1](http://www-eu.apache.org/dist/hadoop/common/hadoop-2.8.0/hadoop-2.8.0.tar.gz) OR [Link 2](http://archive.apache.org/dist/hadoop/core//hadoop-2.8.0/hadoop-2.8.0.tar.gz))
1. Java JDK 1.8.0.zip [Link to download](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

## Set up
1. Check either Java 1.8.0 is already installed on your system or not, use **"Javac -version"** to check. 
![java version]({{site.baseurl}}/assets/img/posts/hadoop/How%20to%20check%20java%20version.png)

1. If Java is not installed on your system then first install java under **"C:\JAVA"**
![Java setup]({{site.baseurl}}/assets/img/posts/hadoop/Java.png)

1. Extract file Hadoop 2.8.0.tar.gz or Hadoop-2.8.0.zip and place under **"C:\Hadoop-2.8.0"**.
![hadoop]({{site.baseurl}}/assets/img/posts/hadoop/Hadoop-2.8.0.png)

1. Set the path HADOOP_HOME Environment variable on windows 10(see Step 1,2,3 and 4 below).
![hadoop]({{site.baseurl}}/assets/img/posts/hadoop/Hadoop%20Path.png)

1. Set the path JAVA_HOME Environment variable on windows 10(see Step 1,2,3 and 4 below).
![java]({{site.baseurl}}/assets/img/posts/hadoop/Java%20Path.png)

1. Next we set the Hadoop bin directory path and JAVA bin directory path.
![bin]({{site.baseurl}}/assets/img/posts/hadoop/bin%20directory%20path.png)

## Configuration
1. Edit file **C:/Hadoop-2.8.0/etc/hadoop/core-site.xml**, paste below xml paragraph and save this file.

```xml
<configuration>
   <property>
       <name>fs.defaultFS</name>
       <value>hdfs://localhost:9000</value>
   </property>
</configuration>
```

2. Rename "mapred-site.xml.template" to "mapred-site.xml" and edit this file **C:/Hadoop-2.8.0/etc/hadoop/mapred-site.xml**, paste below xml paragraph and save this file.

```xml
<configuration>
   <property>
       <name>mapreduce.framework.name</name>
       <value>yarn</value>
   </property>
</configuration>
```

3. Create folder **"data"** under **"C:\Hadoop-2.8.0"**
* Create folder  **"datanode"** under **"C:\Hadoop-2.8.0\data"**
* Create folder  **"namenode"** under **"C:\Hadoop-2.8.0\data"**
![data]({{site.baseurl}}/assets/img/posts/hadoop/data.PNG)
4. Edit file  **C:\Hadoop-2.8.0/etc/hadoop/hdfs-site.xml**, paste below xml paragraph and save this file.

```xml
<configuration>
   <property>
       <name>dfs.replication</name>
       <value>1</value>
   </property>
   <property>
       <name>dfs.namenode.name.dir</name>
       <value>/hadoop-2.8.0/data/namenode</value>
   </property>
   <property>
       <name>dfs.datanode.data.dir</name>
       <value>/hadoop-2.8.0/data/datanode</value>
   </property>
</configuration>
```

5. Edit file **C:/Hadoop-2.8.0/etc/hadoop/yarn-site.xml**, paste below xml paragraph and save this file.

```xml
<configuration>
   <property>
    	<name>yarn.nodemanager.aux-services</name>
    	<value>mapreduce_shuffle</value>
   </property>
   <property>
      	<name>yarn.nodemanager.auxservices.mapreduce.shuffle.class</name>  
	<value>org.apache.hadoop.mapred.ShuffleHandler</value>
   </property>
</configuration>
```

6. Edit file **C:/Hadoop-2.8.0/etc/hadoop/hadoop-env.cmd** by closing the command line  **"JAVA_HOME=%JAVA_HOME%"** instead of set  **"JAVA_HOME=C:\Java"** (On C:\java this is path to file jdk.18.0)

![java path]({{site.baseurl}}/assets/img/posts/hadoop/java%20path%20setup.png)

## Hadoop Configuration
1. Dowload file [Hadoop Configuration.zip](https://github.com/MuhammadBilalYar/HADOOP-INSTALLATION-ON-WINDOW-10/blob/master/Hadoop%20Configuration.zip) 
1. Delete file bin on C:\Hadoop-2.8.0\bin, replaced by file bin on file just download (from Hadoop Configuration.zip).
1. Open cmd and typing command **"hdfs namenode –format"** . You will see 
![hdfs namenode –format]({{site.baseurl}}/assets/img/posts/hadoop/hdfs%20namenode%20%E2%80%93format.PNG)

## Testing
1. Open cmd and change directory to "C:\Hadoop-2.8.0\sbin" and type **"start-all.cmd"** to start apache.
![start all]({{site.baseurl}}/assets/img/posts/hadoop/start-all.PNG)
1. Make sure these apps are running 
* Hadoop Namenode
* Hadoop datanode
* YARN Resourc Manager
* YARN Node Manager
![hadoop nodes]({{site.baseurl}}/assets/img/posts/hadoop/nodes.PNG)
3. Open:  http://localhost:8088
![cluster]({{site.baseurl}}/assets/img/posts/hadoop/hadoop%20cluster.PNG)
4. Open:  http://localhost:50070
![hdfs]({{site.baseurl}}/assets/img/posts/hadoop/hdfs.PNG)
# Congratulations, Hadoop installed.