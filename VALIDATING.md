Validating your virtual machine setup
=====================================

After the `vagrant up` command has completed, you'll have a CentOS
virtual machine with the following installed:

* Hadoop HDFS
* Hadoop YARN
* Hive
* Spark

Let's take a look at each one and validate that it's installed and
setup as expected.

## Hadoop HDFS
## Hadoop YARN
## Hadoop Hive
## Hadoop Spark


SSH into your virtual machine.

    vagrant ssh

Run an example MapReduce job.

    # create a directory for the input file
    hdfs dfs -mkdir wordcount-input

    # generate sample input and write it to HDFS
    echo "hello dear world hello" | hdfs dfs -put - wordcount-input/hello.txt

    # run the MapReduce word count example
    hadoop jar /usr/local/hadoop/share/hadoop/mapreduce/hadoop*example*.jar wordcount wordcount-input wordcount-output

    # validate the output of the job - you should see the following in the output:
    #     dear   1
    #     hello  2
    #     world  1
    hdfs dfs -cat wordcount-output/part*

Create a Hive table over the results of the MapReduce job, and
run a query.

    $ hive
    hive> CREATE EXTERNAL TABLE wordcount (
        word STRING,
        count INT
    )
    ROW FORMAT DELIMITED FIELDS TERMINATED BY '\t'
    LOCATION '/user/vagrant/wordcount-output';

    hive> select * from wordcount order by count;

Run the same query as a Spark job.

    spark-shell --master yarn-client

    val text_file = sc.textFile("hdfs:///user/vagrant/wordcount-input/hello.txt")
    text_file.collect.foreach(println)
    sc.stop
