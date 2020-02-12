# sf-crime-statistics-kafka-pyspark


1. How did changing values on the SparkSession property parameters affect the throughput and latency of the data?

When the size out output returned to driver is high then we can look at modifying the following property.
	Spark.driver.memory

processedRowsPerSecond value need to be tracked when we do any configuration changes. This gives good indication of the system throughput.

Try setting spark.streaming.kafka.maxRatePerPartition to a higher number and see if there is any increase in data ingestion

Try salting or broadcasting to improve join performance

-----------------------

2. What were the 2-3 most efficient SparkSession property key/value pairs? Through testing multiple variations on values, how can you tell these were the most optimal?

Some of the useful configuration properties are :

Spark.executor.memory , 
Spark.driver.memory , 
Spark.sql.shuffle.partitions , 
Spark.default.parallelism

During job submission if the failure happens due to memory issue, you can look at modifying the first 2 properties. Be careful about the size of the final output which is returned to the driver.

Tracking processedRowsPerSecond  value during changes will help in getting optimal settings
