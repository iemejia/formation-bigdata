Homework
========

**Due Date: 18/01/2018**

You must finish the GDELT exercise to calculate the top most relevant countries given their mentions from the TP and send me the following:

1. The source code of your GDELT analysis classes.

2. The output of the execution (part-1-00000, part-2-00000, ...) for the month corresponding to your user account. e.g. if your user account is id05 or gcn05 you must calculate the query for the month 201805. (If your group number is bigger or equal to 12 you must take the files from the previous year e.g. 201712, 201701, 201702 ...).

    Remember that the GDELT dataset is available here:
    http://data.gdeltproject.org/events/index.html

    Download the files corresponding to the month of your pair e.g. 

        wget http://data.gdeltproject.org/events/20180501.export.CSV.zip
        wget http://data.gdeltproject.org/events/20180502.export.CSV.zip
        ...

    Unzip and put the files in HDFS

        unzip "*.zip"

    Create a directory for your month files

        hadoop fs -mkdir -p hdfs:///user/id##/dataset/gdelt/

    Copy the files to HDFS

        hadoop fs -put ./2018##* hdfs:///user/id##/dataset/gdelt/

    Check that the files were copied correctly

        hadoop fs -ls hdfs:///user/id##/dataset/gdelt/

    Execute your analysis

    	hadoop jar JARFILE “hdfs:///user/id##/dataset/gdelt/*”

3. The metrics result after an execution, this is the counter information that the job prints when you execute it (for example):

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

5. Finally you must do a small report (a txt or doc file) explaining your program approach and what are the differences (if there are any) between executing the job locally vs in the cluster with the input on HDFS. If possible execute the job by assigning more CPUs to the VM and explain if the job is partitioned differently and why.
