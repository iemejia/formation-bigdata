Homework
========

Due Date: TBD

You must finish the GDELT exercise to calculate the top most relevant countries given their mentions from the TP and send me the following:

1. The source code of your GDELT analysis classes.

2. The output of the execution (part-1-00000, part-2-00000, ...) for the month corresponding to your user account. e.g. if your user account is id05 or gcn05 you must calculate the query for the month 201705. (If your group is 11 or 12 you must take the files for the previous year e.g. 201611 or 201612).

    Remember that the GDELT dataset is available here:
    http://data.gdeltproject.org/events/index.html

    A summary of how to download and let the files:

    First connect to the cluster

	    ssh id##@ec2….

    Download the files corresponding to the month of your pair e.g. 

        wget http://data.gdeltproject.org/events/20170501.export.CSV.zip
        wget http://data.gdeltproject.org/events/20170501export.CSV.zip
        …

    Unzip and put the files in HDFS

        unzip "*.zip"s
        hadoop fs -mkdir -p hdfs:///user/id##/dataset/gdelt/
        hadoop fs -put 2017##*.CSV hdfs:///user/id##/dataset/gdelt/

    Remove the local files

        rm *.zip
        rm *.CSV

    Execute your analysis

    	hadoop jar JARFILE “hdfs:///user/id##/dataset/gdelt/*”

3. The metrics result after an execution in the cluster, this is the counter information that the job prints when you execute it (for example):

        17/01/13 09:23:18 INFO Job: Counters: 30
            File System Counters
                FILE: Number of bytes read=1142342
                FILE: Number of bytes written=1807987
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
            Map-Reduce Framework
                Map input records=7062
                …

4. The metrics result after running the same program using as input Amazon's S3 GDELT repository. DON'T FORGET TO FILTER FOR THE EXACT MONTH or the job will take longer.

    hadoop jar JARFILE s3://gdelt-open-data/events/201705* hdfs://.../output/...

5. Finally you must do a small report (a txt or doc file) explaining your approach and what are the differences (if there are any) between executing the job locally vs in the cluster with the input on HDFS vs in the cluster with the input in S3.
