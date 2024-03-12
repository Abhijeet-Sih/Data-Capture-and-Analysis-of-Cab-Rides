# Architecture and Approach

The two types of data are the clickstream data and batch data. The clickstream data is captured in Kafka. A streaming framework should consume the data from Kafka and load the same to Hadoop. Once the clickstream data enters the Stream processing layer, it is synced to the HDFS directory to process further. For the batch data, which is the bookings data, the data is stored in the RDS and needs to be ingested to Hadoop.

Also, in cases wherein aggregates need to be prepared, data is read from HDFS, processed by a processing framework such as Spark and written back to HDFS to create a Hive table for the aggregated data.

Once both the data are loaded in HDFS, this data is loaded into Hive tables to make it queryable. Hive tables serve as final consumption tables for end-user querying and are eventually consistent.

![7e96fb01-9f07-4829-9668-dd12802e19c3-Capture8](https://github.com/Abhijeet-Sih/Data-Capture-and-Analysis-of-Cab-Rides/assets/77975708/d749c323-4029-4dca-8646-28636e9cb689)
