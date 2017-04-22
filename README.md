MapReduce
=========

MapReduce implementation for a word count with Apache Hadoop.

##First step:
Download/ create the file you want to search. In our case as example I used: https://www.dropbox.com/s/6yg2xtg10uri3qx/movies.list?dl=0

## Basic usage:
```bash
export JAVA_HOME=/usr/java/default
export PATH=$JAVA_HOME/bin:$PATH
export HADOOP_CLASSPATH=$JAVA_HOME/lib/tools.jar
/usr/bin/hadoop com.sun.tools.javac.Main WordCount.java
jar cf mwc.jar WordCount*.class
hadoop fs -mkdir /user/YourFolder
hadoop fs -mkdir InputWordCount
hadoop fs -copyFromLocal /home/YourFolder/WordCount/movies.list InputWordCount/movies.list
hdfs dfs -ls /user/YourFolder/InputWordCount/
hadoop jar mwc.jar WordCount /user/YourFolder/InputWordCount/ /user/YourFolder/output
hadoop fs -get /user/YourFolder/output /home/YourFolder/WordCount/
hdfs dfs -ls /user/YourFolder/output
hdfs dfs -cat /user/YourFolder/output/part-r-00000
```

Change history
--------------

* **Version 1.0.0.0 (2017-04-22)** : 1.0 release.