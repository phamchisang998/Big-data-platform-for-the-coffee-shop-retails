# Big data platform for the coffee-shop retails
<img src="https://user-images.githubusercontent.com/83225697/121920357-28354180-cd62-11eb-9aef-2ae4b4986ad2.png" />

# What is this?
- This is a bundle of application and code that built upon hadoop ecosystem.
- This system is aimed to store, manage, manipulate and analyze big data of the coffee-shop retailers.
# Overview
- Assume that data will come to realtime-data folder in your pc (you can use DataMoving to move data any other place in you PC as you want).
- Use Nifi to transform and move data into hdfs.
- In HDFS you can use Hive for analytics or map reduce application according to your uses.
- Sqoop is used to export your computed results in hdfs into RDBMS (we use MySQL).
- You can use BI tools that connected to RDBMS data resource for visulization or decision making.
# Requirements
## OS & PC(VMware or Virtualbox).
- Ubuntu 20.04 LTS
- 1 master 16GB Ram, 40GB disk (user: hduser, pc: master).
- 2 slave 2GB Ram, 30GB disk.(user: hduser, pc: slave01/slave02.)
## Hadoop cluster:
- Prepare your hadoop cluster.
- Mapping ip of every pc to the name of this pc, ex: **ip of master** is mapped to name **master**.
- Start and check if your cluster is on the right configuration.
## Hadoop ecosystem
- Hadoop ^3.3.0
- Apache Sqoop ^2.6.0
- Apache Nifi ^1.1.1
- Apache Hive ^2.3.8
## Programming Language
- Java 8
- Python 3.8
- NodeJS 12.22.1
- Shell script
- SQL
- HQL
# How to use
## Data generator
### Install requirements (terminal):
`python3.8 -m pip install requirements.txt`
### Open file generator.py config for simualiton your retailers
- At the opening of the file.
`self.rangeAvgOrderPerHour = [5,20]    # avarage oders every hours.`\
`self.rangeAvgProductPerOrder = [1,5]  # avarage products for every order.`\
`self.folders = '11-1'   #folder output.`\
`self.openTime = 8       # time that your shop open.`\
`self.closeTime = 23     # time that your shop will close.`
- At the end of the file config time range you want to generate.\
`fromDate = '2020-11-25 08:00:00'`\
`toDate = '2021-01-25 07:00:00'`
### Run file (terminal):
`python3 generator.py`
## Nifi
### Import xml file
- Import the flow in your Nifi.
- Config link dir and host.
### Put the script file at the path you config in ExecuteScript Processor.
- You can change the script to transform data as your custom.
- The script can be replace by Python, Groovy,...
## MySQL
- Create DB **aiacad** and grant all privilege to user **hduser** (password: **hduser@123**, host: **%**).
- You can consult this one at your **root** user mysql:
`mysql> CREATE DATABASE aiacad;`\
`mysql> CREATE USER 'hduser'@'%' IDENTIFIED BY 'hduser@123';`\
`mysql> GRANT ALL PRIVILEGES ON hivedb.* TO 'hduser'@'%' WITH GRANT OPTION;`\
`mysql> FLUSH PRIVILEGES;`
## Hive
- Install and config Hive with schematool store metadata in mysql.
- Read file ReadMe to run Hive scripts.
## Sqoop
- Install sqoop in your cluster.
- Read file ReadMe to know how to run script at the right way.
## MapReduce
- You can use .jar file at every folder to run the app according to ReadMe file.
- Or you can change the process and build your own .jar file based on the source code.
# Support
*AI academy - Big data analytics*
