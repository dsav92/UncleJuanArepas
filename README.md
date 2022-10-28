# UncleJuanArepas
This repository contains data and notebook to Uncle Juan business qustion

The goal is to produce a dataset with the hourly averaged metrics for kitchen k1 and machine m1 associated to arepa type a1 in the input time interval (YYYYMM-DDTHH:MM:SS).

We have the datasets:

- Cooking metrics: a table containing cooking metrics
retrieved by each machine associated to phase 1 for each
cooked batch.

- Batch registry: a table containing the main information of
each produced batch.
  
- Faulty intervals: a table containing for each machine
associated to phase 1 the intervals in which metrics data
are note reliable.

In the first step we read data from the three datasets and save them in three Pandas Dataframe. Then we cast the string value of timestamp in Timestamp format for every column of each dataset that contain this values.

Then join Cooking metrics with Batch registry in order to get metrics for every different phase, transforming the string value of float field in Float format.

Now we can filter data in order to get rows about machine 1 (m1) for arepas type 1 (a) in phase 1 (b1).

In order to get the reliable values, we filter out the faulty data starting by Faulty intervals.

To compute the averaged metrics, we collect the metrics for each rows (if is in the specified interval) and then get the average value for the interval in new dataframe. 

Then we also compute the hourly averaged metrics:
- Validate the metrics for the input interval
- Create new dataframe
- Get the time delta for hours from timestamp
- Compute averaged metrics
