vagrant-hadoop-2.7.1-spark-1.4.1-hive-1.2.1
===========================================

# Introduction

Vagrant project to spin up a single virtual machine running:

* Hadoop 2.7.1
* Hive 1.2.1
* Spark 1.4.1

The virtual machine will be running the following services:

* HDFS NameNode + NameNode
* YARN ResourceManager + JobHistoryServer + ProxyServer
* Hive metastore and server2
* Spark history server

# Getting Started

1. [Download and install VirtualBox](https://www.virtualbox.org/wiki/Downloads)
2. [Download and install Vagrant](http://www.vagrantup.com/downloads.html).
3. Run ```vagrant box add centos65 https://github.com/2creatives/vagrant-centos/releases/download/v6.5.1/centos65-x86_64-20131205.box```
4. Git clone this project, and change directory (cd) into this project (directory).
5. Run ```vagrant up``` to create the VM.
6. Execute ```vagrant ssh``` to login to the VM.

# Web user interfaces

Here are some useful links to navigate to various UI's:

* YARN resource manager:  (http://10.211.55.101:8088)
* Job history:  (http://10.211.55.101:19888/jobhistory/)
* HDFS: (http://10.211.55.101:50070/dfshealth.html)
* Spark history server: (http://10.211.55.101:18080)
* Spark context UI (if a Spark context is running): (http://10.211.55.101:4040)

# Validating your virtual machine setup

To test out the virtual machine setup, and for examples of how to run
MapReduce, Hive and Spark, head on over to [VALIDATING.md](VALIDATING.md).

# More advanced setup

If you'd like to learn more about working and optimizing Vagrant then
take a look at [ADVANCED.md](ADVANCED.md).

# Credits

This project is based on the great work carried out at (https://github.com/vangj/vagrant-hadoop-2.4.1-spark-1.0.1).
